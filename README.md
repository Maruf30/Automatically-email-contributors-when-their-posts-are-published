# Automatically-email-contributors-when-their-posts-are-published




function jeba_authorNotification($post_id) {
   $post = get_post($post_id);
   $author = get_userdata($post->post_author);
 
   $message = "
      Hi ".$author->display_name.",
      Your post, ".$post->post_title." has just been published. Well done!
   ";
   wp_mail($author->user_email, "Your article is online", $message);
}
add_action('publish_post', 'jeba_authorNotification');
