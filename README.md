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



$ip = '';
$ch = curl_init('http://ipwho.is/'.$ip);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
curl_setopt($ch, CURLOPT_HEADER, false);
$ipwhois = json_decode(curl_exec($ch), true);
curl_close($ch);
echo $ipwhois['country'] . ' ' . $ipwhois['flag']['emoji'];

----------------------------------------------------------------------------------------------------------->

// Set other options for Custom Post Type
      
    $args = array(
        'label'               => __( 'movies', 'twentytwentyone' ),
        'description'         => __( 'Movie news and reviews', 'twentytwentyone' ),
        'labels'              => $labels,
        // Features this CPT supports in Post Editor
        'supports'            => array( 'title', 'editor', 'excerpt', 'author', 'thumbnail', 'comments', 'revisions', 'custom-fields', ),
        // You can associate this CPT with a taxonomy or custom taxonomy. 
        'taxonomies'          => array( 'genres' ),
        /* A hierarchical CPT is like Pages and can have
        * Parent and child items. A non-hierarchical CPT
        * is like Posts.
        */
        'hierarchical'        => false,
        'public'              => true,
        'show_ui'             => true,
        'show_in_menu'        => true,
        'show_in_nav_menus'   => true,
        'show_in_admin_bar'   => true,
        'menu_position'       => 5,
        'can_export'          => true,
        'has_archive'         => true,
        'exclude_from_search' => false,
        'publicly_queryable'  => true,
        'capability_type'     => 'post',
        'show_in_rest' => true,
  
    );
      
    // Registering your Custom Post Type
    register_post_type( 'movies', $args );
  
}
  
/* Hook into the 'init' action so that the function
* Containing our post type registration is not 
* unnecessarily executed. 
*/
  
add_action( 'init', 'custom_post_type', 0 );



----------------------------------------------------------_>

UPDATE wp_options SET option_value = replace(option_value, 'http://localhost/OTC_Book', 'https://webgarh.co/qtcbook') WHERE option_name = 'home' OR option_name = 'siteurl';
UPDATE wp_posts SET guid = replace(guid, 'http://localhost/OTC_Book','https://webgarh.co/qtcbook');
UPDATE wp_posts SET post_content = replace(post_content, 'http://localhost/OTC_Book', 'https://webgarh.co/qtcbook');
UPDATE wp_postmeta SET meta_value = replace(meta_value,'http://localhost/OTC_Book','https://webgarh.co/qtcbook');


------------------------------------------------------------------------>
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

---------------------------------------------------->

add_filter( 'excerpt_length', 'mytheme_custom_excerpt_length', 999 );
function new_excerpt_more( $more ) {
  return '';
}
add_filter('excerpt_more', 'new_excerpt_more');




----------------------------------------------------------------------------------------------->
add_action( 'manage_posts_extra_tablenav', 'admin_order_list_top_bar_button', 20, 1 );
function admin_order_list_top_bar_button( $which ) {
    global $typenow;


    if ( 'shop_order' === $typenow && 'top' === $which ) {
        ?>
        <div class="alignleft actions custom">
            <button type="submit" name="custom_" style="height:32px;" class="button" value=""><?php
                echo __( 'Custom abc', 'woocommerce' ); ?></button>
        </div>
        <?php
    }
}

function my_custom_columns_list($columns) {
    
    unset( $columns['seopress_title']  );
    unset( $columns['seopress_desc'] );
  


	
    return $columns;
}
add_filter( 'manage_product_posts_columns', 'my_custom_columns_list' );


add_filter( 'manage_edit-product_columns', 'misha_brand_column', 20 );
function misha_brand_column( $columns_array ) {

	// I want to display Brand column just after the product name column
	return array_slice( $columns_array, 0,10, true )
	+ array( 'on_off' => 'Show/Hide' )
	+ array_slice( $columns_array, 10, NULL, true );


}

add_action( 'manage_posts_custom_column', 'misha_populate_brands' );
function misha_populate_brands( $column_name ) {
 global $post;
  
	if( $column_name  == 'on_off' ) {
      $product_enable=get_post_meta($post->ID,'product_enable_disable',true);
    if($product_enable==1){
  $checked='checked';
    }else{
        $checked='';
    }
		// if you suppose to display multiple brands, use foreach();
		/*$x = get_the_terms( get_the_ID(), 'pa_brand'); // taxonomy name
		echo $x[0]->name;*/ 
  
    echo '<label class="switch">
  <input type="checkbox"  '.$checked.' data-pro_id="'.$post->ID.'" class="onetwo '.$product_status.'" value="1" name="check1" >
  <span class="slider round"></span>
</label>';


	}



}

--------------------------------------------------------------------------------------------------------------->

<script> 
jQuery(window).scroll(function(){
      if (jQuery(this).scrollTop() > 135) {
          jQuery('header.x-masthead').addClass('fixed');
      } else {
          jQuery('header.x-masthead').removeClass('fixed');
      }
  });

<?php $url = site_url(); ?>

//var url= window.location.href;  
//alert(url);


//alert(attvalue);

jQuery('.redirect_contact').click(function(){
var attvalue = jQuery('.redirect_contact').attr('myatt');
   window.location.href='<?php echo $url.'/contact/?equipment_rental=';?>'+attvalue;

});
const urlParams = new URLSearchParams(window.location.search);
const param_x = urlParams.get('equipment_rental');
   //alert(param_x);
   jQuery("#equpment_value").append(param_x);
</script>



----------------------------------------------------------------------------->

function delete_post_type(){
  unregister_post_type( 'x-portfolio' );
}
add_action('init','delete_post_type', 100);


--------------------------------------------------------------------->

<div class="related_post">
  <div class="container_width">
<?php

//get the taxonomy terms of custom post type


$terms = get_the_terms($single->ID,'equipment_category');
foreach ($terms as $term ) {
   $term->name;
}
/*echo "<pre>";
print_r($texoname );*/

 
  
//query arguments
$args = array(
    'post_type' => 'equipment_rentals',
    'post_status' => 'publish',
    'posts_per_page' => 5,
    'orderby' => 'rand',

    'tax_query' => array(
        array(
            'taxonomy' => 'equipment_category',
            'field' => 'slug',
            'terms' => $term->name,

        )
    ),
    'post__not_in' => array ($single->ID),
);

//the query
$relatedPosts = new WP_Query( $args );

//loop through query
if($relatedPosts->have_posts()){
    echo '<ul>';
    while($relatedPosts->have_posts()){ 
        $relatedPosts->the_post();
?>
        <li><a href="<?php the_permalink(); ?>"><?php the_title(); ?></a></li>
<?php
    }
    echo '</ul>';
}else{
    //no posts found
}

//restore original post data
wp_reset_postdata();

?>



------------------------------------------------------------------------------>
get_queried_object();




------------------------------------------>

<?php

        $taxonomy = 'equipment_category';
        $terms = get_terms($taxonomy);
        if ( $terms && !is_wp_error( $terms ) ) :
        ?>
        <ul>
            <?php foreach ( $terms as $term ) { ?>
                <li><a href="<?php echo get_term_link($term->slug, $taxonomy); ?>"><?php echo $term->name; ?></a></li>
            <?php } ?>
        </ul>
      <?php endif;?>
      
      
      --------------------------------------------------------->


$args = array(
    'post_type' => 'post',
    'tax_query' => array(
        array(
            'taxonomy' => 'people',
            'field'    => 'slug',
            'terms'    => 'bob',
        ),
    ),
);
$query = new WP_Query( $args );




------------------------------------------------------>













