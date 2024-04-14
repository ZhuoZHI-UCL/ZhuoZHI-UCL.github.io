#如何修改主页上的个人介绍
前往文件D:\OneDrive - University College London\Desktop\求职\Personal website\ZhuoZHI-UCL.github.io\_pages\about.md

#如何修改主页上的照片的上边距
前往文件D:\OneDrive - University College London\Desktop\求职\Personal website\ZhuoZHI-UCL.github.io\_sass\_base.scss
中的Profile类定义 

#修改主页下方图标大小
前往D:\OneDrive - University College London\Desktop\求职\Personal website\ZhuoZHI-UCL.github.io\_sass\_base.scss
修改.social {
  text-align: center;

  .contact-icons {
    font-size: 2rem;

#屏蔽掉blog界面
设置\_pages\blog.md中nav为false

修改project页面所有的文字为原始大小而不是全部小写
修改\_includes\projects.liquid 中  capitalize/uppercase/lowercase

修改project界面预览项目字体大小
在 _sass\_base.scss文件中增加了  
h2.card-title {
    font-size: 10px; // 定义非hover状态下的字体大小
  }
这个字体的大小可以自定义

修改project界面右边 PhD, Master, Bachelor的颜色
在_sass\_base.scss文件中修改
 h2.category {
    color: $black-color;

修改publications右边年份颜色
在_sass\_base.scss文件中修改
h2.bibliography {
    // color: var(--global-divider-color);
    color: $black-color;

去掉每一个页面上显示该页面的名字
在_layouts\page.liquid 中注释掉了一部分，注释用的方法是
{% comment %}
{% endcomment %}