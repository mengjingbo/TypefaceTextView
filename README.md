# TypefaceTextView
利用```Typeface```显示.ttf文件中的字符在TextView上面。
##### 效果图：
##### 代码如下：
```
  /**
   * 作者：僧格洛卓 
   * 描述：TypefaceTextView
   */
  public class TypefaceTextView extends TextView {

      public TypefaceTextView(Context context) {
          super(context);
          init(context, null);
      }

      public TypefaceTextView(Context context, @Nullable AttributeSet attrs) {
          super(context, attrs);
          init(context, attrs);
      }

      private void init(Context context, AttributeSet attrs) {
          // 自定义属性
          TypedArray mArray = context.obtainStyledAttributes(attrs, R.styleable.TypefaceTextView);
          String mTypefacePath = mArray.getString(R.styleable.TypefaceTextView_typefacePath);
          String mTypefaceUnicode = mArray.getString(R.styleable.TypefaceTextView_typefaceUnicode);
          mArray.recycle();
          if (!TextUtils.isEmpty(mTypefacePath) && !TextUtils.isEmpty(mTypefaceUnicode)) {
              setTypeface(Typeface.createFromAsset(context.getAssets(), mTypefacePath));
              setText(mTypefaceUnicode);
          }
      }
  }
```
##### 自定义属性：
```
    <declare-styleable name="TypefaceTextView">
        <!--assets文件夹下的.ttf文件地址-->
        <attr name="typefacePath" format="string" />
        <!--Unicode码-->
        <attr name="typefaceUnicode" format="reference|string" />
    </declare-styleable>
```
##### 在布局中使用：
```
  <?xml version="1.0" encoding="utf-8"?>
  <LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
     xmlns:typefacetext="http://schemas.android.com/apk/res-auto"
     android:layout_width="match_parent"
     android:layout_height="wrap_content"
     android:background="@color/white"
     android:gravity="center"
     android:orientation="horizontal">

    <com.example.app.view.widget.TypefaceTextView
        android:id="@+id/navigation_home"
        android:layout_width="0dp"
        android:layout_height="match_parent"
        android:layout_weight="1"
        android:gravity="center"
        android:padding="5dp"
        android:textColor="@color/gray"
        android:textSize="25dp"
        typefacetext:typefacePath="navigation/home_page_navigation.ttf"
        typefacetext:typefaceUnicode="@string/icon_home" />

    <com.example.app.view.widget.TypefaceTextView
        android:id="@+id/navigation_search"
        android:layout_width="0dp"
        android:layout_height="match_parent"
        android:layout_weight="1"
        android:gravity="center"
        android:padding="5dp"
        android:textColor="@color/gray"
        android:textSize="25dp"
        typefacetext:typefacePath="navigation/home_page_navigation.ttf"
        typefacetext:typefaceUnicode="@string/icon_search" />

    <com.example.app.view.widget.TypefaceTextView
        android:id="@+id/navigation_message"
        android:layout_width="0dp"
        android:layout_height="match_parent"
        android:layout_weight="1"
        android:gravity="center"
        android:padding="5dp"
        android:textColor="@color/gray"
        android:textSize="25dp"
        typefacetext:typefacePath="navigation/home_page_navigation.ttf"
        typefacetext:typefaceUnicode="@string/icon_message" />

    <com.example.app.view.widget.TypefaceTextView
        android:id="@+id/navigation_user"
        android:layout_width="0dp"
        android:layout_height="match_parent"
        android:layout_weight="1"
        android:gravity="center"
        android:textColor="@color/gray"
        android:textSize="20dp"
        typefacetext:typefacePath="navigation/home_page_navigation.ttf"
        typefacetext:typefaceUnicode="@string/icon_user" />
</LinearLayout>
```
> 属性说明：
```
typefacetext:typefacePath="navigation/home_page_navigation.ttf"
```
navigation/home_page_navigation.ttf 为assets文件夹下.ttf文件
```
typefacetext:typefaceUnicode="@string/icon_home" 
```
@string/icon_home 为string中的Unicode字符码

案例中Unicode对应的string
```
  <resources>
    <string name="icon_home">&#xe6a9;</string>
    <string name="icon_search">&#xe674;</string>
    <string name="icon_message">&#xe64b;</string>
    <string name="icon_user">&#xe662;</string>
  </resources>
```
