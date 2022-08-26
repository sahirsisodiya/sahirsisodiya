function themename_customize_register($wp_customize){
     
    $wp_customize->add_section('themename_color_scheme', array(
        'title'    => __('Color Scheme', 'themename'),
        'description' => '',
        'priority' => 120,
    ));
  
    //  =============================
    //  = Text Input                =
    //  =============================
    $wp_customize->add_setting('themename_theme_options[text_test]', array(
        'default'        => 'value_xyz',
        'capability'     => 'edit_theme_options',
        'type'           => 'option',
  
    ));
  
    $wp_customize->add_control('themename_text_test', array(
        'label'      => __('Text Test', 'themename'),
        'section'    => 'themename_color_scheme',
        'settings'   => 'themename_theme_options[text_test]',
    ));
  
    //  =============================
    //  = Radio Input               =
    //  =============================
    $wp_customize->add_setting('themename_theme_options[color_scheme]', array(
        'default'        => 'value2',
        'capability'     => 'edit_theme_options',
        'type'           => 'option',
    ));
  
    $wp_customize->add_control('themename_color_scheme', array(
        'label'      => __('Color Scheme', 'themename'),
        'section'    => 'themename_color_scheme',
        'settings'   => 'themename_theme_options[color_scheme]',
        'type'       => 'radio',
        'choices'    => array(
            'value1' => 'Choice 1',
            'value2' => 'Choice 2',
            'value3' => 'Choice 3',
        ),
    ));
  
    //  =============================
    //  = Checkbox                  =
    //  =============================
    $wp_customize->add_setting('themename_theme_options[checkbox_test]', array(
        'capability' => 'edit_theme_options',
        'type'       => 'option',
    ));
  
    $wp_customize->add_control('display_header_text', array(
        'settings' => 'themename_theme_options[checkbox_test]',
        'label'    => __('Display Header Text'),
        'section'  => 'themename_color_scheme',
        'type'     => 'checkbox',
    ));
  
  
    //  =============================
    //  = Select Box                =
    //  =============================
     $wp_customize->add_setting('themename_theme_options[header_select]', array(
        'default'        => 'value2',
        'capability'     => 'edit_theme_options',
        'type'           => 'option',
  
    ));
    $wp_customize->add_control( 'example_select_box', array(
        'settings' => 'themename_theme_options[header_select]',
        'label'   => 'Select Something:',
        'section' => 'themename_color_scheme',
        'type'    => 'select',
        'choices'    => array(
            'value1' => 'Choice 1',
            'value2' => 'Choice 2',
            'value3' => 'Choice 3',
        ),
    ));
  
  
    //  =============================
    //  = Image Upload              =
    //  =============================
    $wp_customize->add_setting('themename_theme_options[image_upload_test]', array(
        'default'           => 'image.jpg',
        'capability'        => 'edit_theme_options',
        'type'           => 'option',
  
    ));
  
    $wp_customize->add_control( new WP_Customize_Image_Control($wp_customize, 'image_upload_test', array(
        'label'    => __('Image Upload Test', 'themename'),
        'section'  => 'themename_color_scheme',
        'settings' => 'themename_theme_options[image_upload_test]',
    )));
  
    //  =============================
    //  = File Upload               =
    //  =============================
    $wp_customize->add_setting('themename_theme_options[upload_test]', array(
        'default'           => 'arse',
        'capability'        => 'edit_theme_options',
        'type'           => 'option',
  
    ));
  
    $wp_customize->add_control( new WP_Customize_Upload_Control($wp_customize, 'upload_test', array(
        'label'    => __('Upload Test', 'themename'),
        'section'  => 'themename_color_scheme',
        'settings' => 'themename_theme_options[upload_test]',
    )));
  
  
    //  =============================
    //  = Color Picker              =
    //  =============================
    $wp_customize->add_setting('themename_theme_options[link_color]', array(
        'default'           => '#000',
        'sanitize_callback' => 'sanitize_hex_color',
        'capability'        => 'edit_theme_options',
        'type'           => 'option',
  
    ));
  
    $wp_customize->add_control( new WP_Customize_Color_Control($wp_customize, 'link_color', array(
        'label'    => __('Link Color', 'themename'),
        'section'  => 'themename_color_scheme',
        'settings' => 'themename_theme_options[link_color]',
    )));
  
  
    //  =============================
    //  = Page Dropdown             =
    //  =============================
    $wp_customize->add_setting('themename_theme_options[page_test]', array(
        'capability'     => 'edit_theme_options',
        'type'           => 'option',
  
    ));
  
    $wp_customize->add_control('themename_page_test', array(
        'label'      => __('Page Test', 'themename'),
        'section'    => 'themename_color_scheme',
        'type'    => 'dropdown-pages',
        'settings'   => 'themename_theme_options[page_test]',
    ));
 
    // =====================
    //  = Category Dropdown =
    //  =====================
    $categories = get_categories();
    $cats = array();
    $i = 0;
    foreach($categories as $category){
        if($i==0){
            $default = $category->slug;
            $i++;
        }
        $cats[$category->slug] = $category->name;
    }
  
    $wp_customize->add_setting('_s_f_slide_cat', array(
        'default'        => $default
    ));
    $wp_customize->add_control( 'cat_select_box', array(
        'settings' => '_s_f_slide_cat',
        'label'   => 'Select Category:',
        'section'  => '_s_f_home_slider',
        'type'    => 'select',
        'choices' => $cats,
    ));
}
  
add_action('customize_register', 'themename_customize_register');



--------------------------------------------------------------------------------------------------------------------__>
UPDATE wp_options SET option_value = replace(option_value, 'http://localhost/OTC_Book', 'https://webgarh.co/qtcbook') WHERE option_name = 'home' OR option_name = 'siteurl';
UPDATE wp_posts SET guid = replace(guid, 'http://localhost/OTC_Book','https://webgarh.co/qtcbook');
UPDATE wp_posts SET post_content = replace(post_content, 'http://localhost/OTC_Book', 'https://webgarh.co/qtcbook');
UPDATE wp_postmeta SET meta_value = replace(meta_value,'http://localhost/OTC_Book','https://webgarh.co/qtcbook');

--------------------------------------------------------------------___>

add_action( 'wp_footer', 'your_function' );

  
function service_list(){
  ob_start();
  get_template_part('services');
  return ob_get_clean();
}

add_shortcode('services_list', 'service_list');
function alternating_post_class($classes) {
    global $wp_query;
    $classes[] = ( $wp_query->current_post%2 === 0 ? 'odd' : 'even' );
    return $classes;
}
add_filter('post_class', 'alternating_post_class');

function mytheme_custom_excerpt_length( $length ) {
    return 20;
}
add_filter( 'excerpt_length', 'mytheme_custom_excerpt_length', 999 );
function new_excerpt_more( $more ) {
  return '';
}
add_filter('excerpt_more', 'new_excerpt_more');


-------------------------------------------------------------->

function alternating_post_class($classes) {
    global $wp_query;
    $classes[] = ( $wp_query->current_post%2 === 0 ? 'odd' : 'even' );
    return $classes;
}
add_filter('post_class', 'alternating_post_class');


---------------------------------------------_>
<?php
$paged = ( get_query_var( 'paged' ) ) ? get_query_var( 'paged' ) : 1;
$args = array(
     'post_type' => 'custom_post_type_name',
     'posts_per_page' => 10,
     'paged' => $paged
);
$loop = new WP_Query( $args );
while ( $loop->have_posts() ) : $loop->the_post();
     // CPT content
endwhile;
?>
<div class="pagination">
     <?php
     $big = 999999999;
     echo paginate_links( array(
          'base' => str_replace( $big, '%#%', get_pagenum_link( $big ) ),
          'format' => '?paged=%#%',
          'current' => max( 1, get_query_var('paged') ),
          'total' => $loop->max_num_pages,
          'prev_text' => '&laquo;',
          'next_text' => '&raquo;'
     ) );
?>
</div>
<?php wp_reset_postdata(); ?>

--------------------------------------------------------->

$(window).scroll(function(){
      if ($(this).scrollTop() > 135) {
          $('#task_flyout').addClass('fixed');
      } else {
          $('#task_flyout').removeClass('fixed');
      }
  });
  
  
  ---------------------------------------------------->











