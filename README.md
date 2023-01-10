# Wordpress

- WordPress là một mã nguồn mở [Content Management System (CMS)](https://en.wikipedia.org/wiki/Content_management_system), Nó cho phép chúng ta xây dựng một trang web động hoặc những blog động. Hiện tại WP là hệ thống blogging phổ biến nhất trên internet và nó cho phép chúng ta update, customize và manage website từ back-end CMS và những components.

## Features

- User Management:
  > Nó cho phép chúng ta quản lý thông tin người dùng như là thay đổi vai trò của người dùng như (admin, user), hoặc đơn giản hơn là những hành động CRUD thông tin của người dùng. vai trò chính của User Management là Authentication.
- Media Management:
  > Đây là một công cụ giúp chúng ta quản lý những file media và thư mục, điều này giúp chúng ta dễ dàng upload và tổ chức và quản lý thư mục trên website của chúng ta.
- Theme System:
  > Chức năng này cho phép chúng ta chỉnh sửa site view và nó bao gồm hình ảnh, stylesheet, template files và custom page.
- Extend with Plugins:
  > Một số plugin có sẵn cung cấp các chức năng và tính năng tùy chỉnh theo nhu cầu của người dùng.
- Search Engine Optimization(SEO):
  > Nó cung cấp một số công cụ tối ưu hóa công cụ tìm kiếm (SEO) giúp SEO trở nên đơn giản hơn.
- Multilingual :
  > Nó cho phép dịch toàn bộ nội dung sang ngôn ngữ mà người dùng muốn.
- Importers :
  > Nó cho phép nhập dữ liệu dưới dạng bài viết. Nó import các custom files, comments, post pages and tags.

## Core files structure

- Cấu trúc thư mục WP được chia làm 2 phần chính core file và content file

### Core file

- Bao gồm các thư mục và tệp tin sau:
- **wp-admin**:
  > Thư mục wp-admin chứa hầu hết các tệp cung cấp chức năng cho WordPress Dashboard. Các tập tin bên trong nó chứa hầu hết các tính năng đã được included. Thư mục này chứa rất nhiều tệp cốt lỗi của WordPress, nhưng mối quan tâm của chúng tôi nằm ở một tệp cụ thể **admin.php**
- **admin.php**:
  > Tệp admin.php nằm ở trung tâm của thư mục wp-admin. Nó cho phép bất kỳ số lượng tính năng quan trọng nào, bao gồm kết nối với cơ sở dữ liệu và tải trang tổng quan. Nó thậm chí còn kiểm tra xem người dùng có quyền quản trị hay không.
- **wp-content**
  > Được người dùng thêm vào dưới dạng chủ đề, plugin và hình ảnh.
- **wp-includes**
  > Thư mục này về cơ bản lưu trữ phần còn lại của các tệp cho phép trang web WordPress của chúng ta hoạt động. Nếu chúng ta mở thư mục, chúng ta sẽ tìm thấy hơn 100 tệp đầu tiên. Nhưng chúng tôi sẽ tập trung vào một trong những tệp quan trọng nhất trong tất cả các tệp cốt lõi của WordPress – **functions.php**
- **functions.php** 
  >**functions.php** hoạt động giống như một plugin WordPress. Nó cho phép chúng ta thêm chức năng vào trang web của mình bằng cách gọi pre-defined functions, và thậm chí tạo chức năng riêng . Ngoài ra, mỗi theme sẽ đi cùng với 1 **functions.php** riêng cho phép chúng ta thêm các tính năng phụ thuộc vào theme vào trang web của mình. Nó hoạt động tách biệt với chức năng nằm trong **wp-includes** và các chức năng đó chỉ hoạt động miễn là theme của chúng ta hoạt động.
- .htaccess
  > Kiểm soát quyền truy cập vào các tệp, thư mục và cấu trúc permalink tổng thể của chúng ta.
- wp-config.php
  > Đây là file config. Bao gồm các cài đặt WordPress cơ bản, cấu hình cơ sở dữ liệu và cập nhật tự động.

## Loop trong WP

> Vòng lặp WordPress hoặc đơn giản là vòng lặp, là code PHP các bài đăng trên WordPress. Vòng lặp được sử dụng trong các WordPress theme để hiển thị danh sách các post trên trang web.

- Code PHP được viết trong Block có mở đầu là `<?php` và kết thúc là `?>`
- Một số câu lệnh loop hay thường được sử dụng là if và while
- Example:

```php
<?php
// checks if there are any posts that match the query
if (have_posts()) :
  // If there are posts matching the query then start the loop
  while ( have_posts() ) : the_post();
    // the code between the while loop will be repeated for each post
    ?>
    <h2 id="post-<?php the_ID(); ?>"><a href="<?php the_permalink() ?>" rel="bookmark" title="Permanent Link to <?php the_title(); ?>"><?php the_title(); ?></a></h2>
    <p class="date-author">Posted: <?php the_date(); ?> by <?php the_author(); ?></p>
    <?php the_content(); ?>
    <p class="postmetadata">Filed in: <?php the_category(); ?> | Tagged: <?php the_tags(); ?> | <a href="<?php comments_link(); ?>" title="Leave a comment">Comments</a></p>
    <?php
    // Stop the loop when all posts are displayed
 endwhile;
// If no posts were found
else :
?>
<p>Sorry no posts matched your criteria.</p>
<?php
endif;
?>
```

## Template Files

### Template Terminology

- **Classic themes**: Template Tags được build ở WordPress functions chúng ta có thể sử dụng trong template file để nhận và hiển thị dữ liệu (như là the_title() and the_content()).
- **Block theme themes**: Sử dụng block thay vì template tags

### Template files

- Các WordPress theme được tạo thành từ các tệp mẫu.
- Trong **classic themes** các file PHP có nội dung bao gồm HTML, Template Tags và PHP code.
- Trong **block themes** chứa các tệp HTML chứa HTML markup đại diện cho các block.

### Template partials

- **header.php** || **header.html** được sử dụng cho site header
- **footer.php** || **footer.html** được sử dụng cho site footer
- **sidebar.php** || **sidebar.html** được sử dụng cho site sidebar
  Ở block themes, template parts phải được đặt trong thư mục được gọi là parts

### Common WordPress template files

- [Common WordPress template files](https://developer.wordpress.org/themes/basics/template-files/#common-wordpress-template-files)

### Using template files

- **Classic theme**
  Ex:
  --Để include header, sử dụng get_header()
  --Để include sidebar, sử dụng get_sidebar()
  --Để include footer, sử dụng get_footer()
  --Để include search form, sử dụng get_search_form()
  --Để include custom theme files, sử dụng get_template_part()
- **Block theme**
  Ex:

```
<!-- wp:template-part {"slug":"header"} /-->
(your page content)
<!-- wp:template-part {"slug":"footer"} /-->

```
Để include search form, sử dụng block markup cho search block
```
<!-- wp:search {"label":"Search","buttonText":"Search"} /-->
```
## the_title() & get_the_title()
- [**the_title()**](https://developer.wordpress.org/reference/functions/the_title/)\
```the_title( string $before = '', string $after = '', bool $echo = true ): void|string```
- Parameters
_$before_ : string Optional
    > Markup cho phía trước title ex: <h1>.
- Default: ""
- _$after_ : string Optional.
    > Markup to phía sau title ex: </h1>
- Default: ''
- _$echo_ : bool Optional
Default: true

**Usage**
- Sử dụng the_title khi chúng ta muốn hiển thị tất cả các bài viết của blog.
Điều này sẽ yêu cầu một vòng lặp, cụ thể là vòng lặp while.
Do đó, the_title được cho là được viết bên trong vòng lặp.


- [**get_the_title()**](https://developer.wordpress.org/reference/functions/the_title/)\
```get_the_title( int|WP_Post $post ): string```
- Parameters
_$post_ : int|WP_Post Optional
    >  Post ID or WP_Post object
Default is global $post.

Return _string_

**Usage**
- Đượng sử dụng để lấy title của một bài post đã biết ID.
ex: 
``` php
<?php echo get_the_title(15);?> 
```
## get_stylesheet_directory_uri() & get_stylesheet_directory()
- [**get_stylesheet_directory_uri()**](https://developer.wordpress.org/reference/functions/get_stylesheet_directory_uri/)
- Được dùng để truy xuất stylesheet directory **URI** cho theme đang hoạt động\
Return \
    _string_ URI to active theme's stylesheet directory.\
ex:
```php
<img src="<?php echo get_stylesheet_directory_uri(); ?>/images/aternus.png" alt="" width="" height="" />

```
- [**get_stylesheet_directory()**](https://developer.wordpress.org/reference/functions/get_stylesheet_directory/)
- Được dùng để truy xuất stylesheet directory **path** cho theme đang hoạt động\
Return\
    _string_ Path to active theme's stylesheet directory.\
ex:
```php
<?php include( get_stylesheet_directory() . '/includes/myfile.php' ); ?>
```
