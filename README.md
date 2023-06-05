# Wordpress-DB-Analysis

## Images and content were taken from https://codex.wordpress.org/Database_Description .

![Untitled](https://github.com/InkiStark/Wordpress-DB-Analysis/assets/116667541/4e927678-8747-4395-9df3-35019531109d)

The above image displays the tables and relations between them which is created upon installing WordPress.

## Database Structure

Upon installing WordPress, in database which is created there are 12 initially tables.
The oreder they are created is random, therefore the following list is randomly numbered.

### The first table is wp_commentmeta. </br>
This table stores addition metadata or infromation related to comments on WordPress sites.</br>
It is used to store supplementary data associated with individual comments.</br>
It provides flexibility for storing additional information or custom fields for comments in WordPress.</br>
It allows developers and site owners to extend the default comment functionality anmd store relevant data associated with comments.</br>

The fields that are created into the table are:</br>
<ins>meta_id</ins>: A unique identifier for each comment meta entry.</br>
<ins>comment_id</ins>: The ID of the comment to which the meta data belongs. </br>
<ins>meta_key</ins>: The key or name of the meta data.</br>
<ins>meta_value</ins>: The value associated with the meta data key.</br>
The primary key for this table is <ins>meta_id.</br>

### Relations to other tables:</br>
wp_commentmeta is related to wp_comments through the comment_id field which serves as a foreign key. The relationship between them is one-to-many!</br>
The comment_id column in wp_commentmeta corresponds to the comment_ID column in wp_comments, establishing a relationship between comments and their associated metadata.</br>
One comment can have multiple metadata entries in the wp_commentmeta table, but each metadata entry corresponds to only one comment in the wp_comments table.</br>

![2](https://github.com/InkiStark/Wordpress-DB-Analysis/assets/116667541/608bbfa0-6098-4922-b62d-86fff5728829)

### Next table is wp_comments.
This table is a core database table that stores information about comments made on a WordPress site.</br>  
It is a fundamental part of the WordPress database schema and is used to store data related to user-generated comments on various types of content, such as posts, pages, or custom post types.</br>
It serves as a repository for all comment-related data, including the comment content, author information, timestamps, and approval status.</br>
he <ins>wp_comments</ins> table provides the foundation for comment management in the WordPress admin dashboard. It allows administrators to review, moderate, edit, delete, and respond to comments posted on their site.</br>

The fields that are created into the table are:</br>
<ins>comment_ID</ins>: A unique identifier for each comment.</br>
<ins>comment_post_ID</ins>: The ID of the post or content to which the comment is associated.</br>
<ins>comment_author</ins>: The name or username of the comment author.</br>
<ins>comment_author_email</ins>: The email address of the comment author.</br>
<ins>comment_author_url</ins>: The URL or website of the comment author.</br>
<ins>comment_author_IP</ins>: The IP address of the comment author.</br>
<ins>comment_date</ins>: The date and time when the comment was posted.</br>
<ins>comment_content</ins>: The actual content or text of the comment.</br>
<ins>comment_approved</ins>: The approval status of the comment.</br>
<ins>comment_parent</ins>: The ID of the parent comment if the comment is a reply to another.</br>
<ins>user_id</ins>: The ID of the user who made the comment if they were logged in.</br>

### Relations to other tables:
The wp_comments table is linked to other tables in the WordPress database with comment_post_ID column relates to the primary key of the wp_posts table, </br>
connecting each comment to the specific post or content it belongs to.</br>
And comment_parent column establishes relationships between comments, enabling threaded or nested comment structures.</br>
Both of the above relationships are described as one-to-many!</br>
One post can have multiple comments, and each comment can have multiple child comments (replies), but each comment belongs to only one post and each child comment has only one parent comment.</br>

![3](https://github.com/InkiStark/Wordpress-DB-Analysis/assets/116667541/22d00bef-5916-4d2f-a676-6f9ccfa6e1ba)

### Next table is wp_links.
This table was used to store information about links or bookmarks.However,after the 3.5 version was released, the table is no longer created by default during WordPress installation. Therefore the link functionality has been deprecated in favor of using the more flexible Custom Post Types (CPT) feature.</br>
Custom post types are specific post types that have been added to WordPress using custom code or plugins. The idea is that you may want to add additional functionality to your site but don't want to add everything as a standard post.</br>

The fields that are created into the table are:</br>
<ins>link_id</ins>: A unique identifier for each link entry.</br>
<ins>link_url</ins>: The URL of the link.</br>
<ins>link_name</ins>: The name or title of the link.</br>
<ins>link_image</ins>: An optional image associated with the link.</br>
<ins>link_target</ins>: The target attribute for the link (e.g., _blank, _self).</br>
<ins>link_description</ins>: A description or brief text about the link.</br>
<ins>link_visible</ins>: The visibility status of the link (e.g., visible or hidden).</br>
<ins>link_owner</ins>: The user ID of the link owner.</br>
<ins>link_rating</ins>: An optional rating or score for the link.</br>
<ins>link_updated</ins>: The date and time when the link was last updated.</br>
<ins>link_rel</ins>: Optional relationship information for the link (e.g., nofollow, bookmark).</br>

### Relations to other tables:
The wp_links table does not have direct relationships with other WordPress core tables. However, it may have been utilized by plugins or themes to establish relationships with other tables for custom functionality related to links.</br>

![4](https://github.com/InkiStark/Wordpress-DB-Analysis/assets/116667541/a8af3912-ac7f-4360-95cd-de5956ded3e4)

### Next table is wp_options:
This table stores various site-wide setting and configuration options for a WordPress installation.It serves as key-value store, </br>
where each option is identified by a unique option name and contains a corresponding option value. </br>

The fields that are created into the table are:</br>
<ins>option_id</ins>: A unique identifier for each option entry.</br>
<ins>option_name</ins>: The name or key of the option.</br>
<ins>option_value</ins>: The value associated with the option.</br>
<ins>autoload</ins>: Indicates whether the option should be automatically loaded or not.</br>
<ins>option_updated</ins>: The date and time when the option was last updated.</br>

### Relations to other tables:
The wp_options table does not have direct relationships with other tables in the WordPress database.</br>
However, certain options stored in the wp_options table may refer to specific database tables or other entities within the WordPress system.

![5](https://github.com/InkiStark/Wordpress-DB-Analysis/assets/116667541/2e081534-742b-4024-9e77-560c54e04466)

### Next table is wp_postmeta.
This is a core database table that stores additional metadata or custom fields associated with posts,pages, and other custom post types.</br>
It provides flexible way to extend the default post structure and store extra information for individual post.</br>

The fields that are created into the table are:</br>
<ins>meta_id</ins>: A unique identifier for each post meta entry.</br>
<ins>post_id</ins>: The ID of the post to which the meta data belongs.</br>
<ins>meta_key</ins>: The key or name of the meta data.</br>
<ins>meta_value</ins>: The value associated with the meta data key.</br>

### Relations to other tables:
The wp_postmeta table is related to the wp_posts table through the post_id column, which serves as a foreign key. </br>
The post_id column in wp_postmeta corresponds to the ID column in wp_posts, establishing a relationship between posts and their associated metadata.</br>
The relationship between the wp_postmeta table and the wp_posts table is a one-to-many.</br>
In this relationship, each post in the wp_posts table can have multiple associated metadata entries in the wp_postmeta table.</br>
The ID column in the wp_posts table serves as the primary key, uniquely identifying each post. The post_id column in the wp_postmeta table serves as a foreign key, referencing the ID column in wp_posts.

![6](https://github.com/InkiStark/Wordpress-DB-Analysis/assets/116667541/1d60cba8-7177-4a24-910a-15515dcdf3e2)


### Next table is wp_posts:
This table is also a core one for WordPress. It stores information about posts,pages,attachments, and other types of content on a WordPress site.</br>
It is one of the most important tables in the WordPress database schema, serving as the central repository for content-related data.</br>
Is primarily used to store blog posts and static pages. Each entry represents a specific piece of content with its associated data, such as author, title, content, date, and more.</br>
Also stores information about media attachments, such as images, videos, or audio files, uploaded to the WordPress media library. These attachments are associated with specific posts or pages.</br>
Can also store content related to custom post types, which are extensions of the default post and page functionality.

The fields that are created into the table are:</br>
<ins>ID</ins>: A unique identifier for each post or content entry.
<ins>post_author</ins>: The user ID of the post author.
<ins>post_date</ins>: The date and time when the post was created.
<ins>post_date_gmt</ins>: The GMT/UTC date and time when the post was created.
<ins>post_content</ins>: The content or text of the post.
<ins>post_title</ins>: The title of the post.
<ins>post_excerpt</ins>: An optional excerpt or summary of the post.
<ins>post_status</ins>: The status of the post (e.g., published, draft, pending, private).
<ins>comment_status</ins>: The comment status for the post (e.g., open, closed).
<ins>ping_status</ins>: The pingback/trackback status for the post (e.g., open, closed).
<ins>post_password</ins>: An optional password to protect the post.
<ins>post_name</ins>: The post's slug or URL-friendly name.
<ins>to_ping</ins>: A list of URLs to ping for the post.
<ins>pinged</ins>: A list of URLs that have been pinged for the post.
<ins>post_modified</ins>: The date and time when the post was last modified.
<ins>post_modified_gmt</ins>: The GMT/UTC date and time when the post was last modified.
<ins>post_content_filtered</ins>: The filtered version of the post content.
<ins>post_parent</ins>: The ID of the parent post if the post is a child or attachment.
<ins>guid</ins>: The globally unique identifier for the post.
<ins>menu_order</ins>: The order of the post in relation to other posts.
<ins>post_type</ins>: The type of content (e.g., post, page, attachment, custom post type).
<ins>post_mime_type</ins>: The MIME type of the post attachment (for attachment posts).
<ins>comment_count</ins>: The number of comments associated with the post.

### Relations to other tables:
The wp_posts table is linked with wp_users table with the post_author which serves as a primary key,connecting each post to the user who created it.</br>
post_parent column establishes relationships between posts, allowing for hierarchical structures and attachments.</br>
ID column is referenced by other tables, such as wp_postmeta, wp_comments, and wp_term_relationships, to establish relationships.
It has two types of relationships.</br>
One-to-Many Relationship:</br>
The wp_posts table has a one-to-many relationship with the wp_postmeta table. Each post in the wp_posts table can have multiple associated metadata entries in the wp_postmeta table.</br>
The relationship is established through the ID column in wp_posts and the post_id column in wp_postmeta.</br>
The wp_posts table has a one-to-many relationship with the wp_comments table.</br>
Each post can have multiple comments associated with it. The relationship is established through the ID column in wp_posts and the comment_post_ID column in wp_comments.</br>
Many-to-One Relationship:</br>
The wp_posts table has a many-to-one relationship with the wp_users table.</br>
Multiple posts can be authored by the same user. The relationship is established through the post_author column in wp_posts and the ID column in wp_users.</br>

![7](https://github.com/InkiStark/Wordpress-DB-Analysis/assets/116667541/b72b9b9e-4012-4d3c-946a-862a756eb413)


### Next table is wp_terms:
Is a table that stores the taxonomy terms used to categorize and clasify content on a WordPress site.</br>
It serves as a central repository to the terms associated with different taxonomies, such as categories,tags,or any custom taxonomies defined for a site.</br>
The wp_terms table is primarily used to store the terms associated with the built-in taxonomies of categories and tags. Each category or tag corresponds to a term entry in the wp_terms table.</br>

The fields that are created into the table are:</br>
<ins>term_id</ins>: A unique identifier for each term.</br>
<ins>name</ins>: The name or label of the term.</br>
<ins>slug</ins>: The slug or URL-friendly version of the term name.</br>
<ins>term_group</ins>: An optional field used for grouping terms.</br>
<ins>term_taxonomy_id</ins>: A unique identifier for the term in the context of a specific taxonomy.</br>

### Relations to other tables:</br>
The wp_terms table is linked to wp_term_taxonomy with the term_taxonomy_id.</br>
The wp_terms table has a one-to-many relationship with the wp_term_taxonomy table. </br>
Each term in the wp_terms table can have multiple associated taxonomy entries in the wp_term_taxonomy table.</br>
The relationship is established through the term_taxonomy_id field in wp_terms and the term_taxonomy_id field in wp_term_taxonomy.</br>

![8](https://github.com/InkiStark/Wordpress-DB-Analysis/assets/116667541/04744837-743c-400a-bd6a-36bd3dfcafaf)

### Next table is wp_termmeta:
wp_termmeta table does not exist in a default WordPress installation.</βρ>
However, it is worth noting that starting from WordPress version 4.4, the WordPress core provides the capability to add metadata to terms through the wp_termmeta table.

The fields that are created into the table are:</br>
<ins>meta_id</ins>: A unique identifier for each term meta entry.</br>
<ins>term_id</ins>: The ID of the term to which the meta data belongs.</br>
<ins>meta_key</ins>: The key or name of the meta data.</br>
<ins>meta_value</ins>: The value associated with the meta data key.</br>

### Relations to other tables:</br>
The wp_termmeta table is related to the wp_terms table through the term_id column, which serves as a foreign key. </br>
The term_id column in wp_termmeta corresponds to the term_id column in wp_terms, establishing a one-to-many relationship between terms and their associated metadata.</br>

![9](https://github.com/InkiStark/Wordpress-DB-Analysis/assets/116667541/b6a9198d-f9e6-4e19-a57b-0248f180bb19)

### Next table is wp_term_relationships:
This is a table that establishes relationships between content items (such as posts, pages, or custom post types) and taxonomy terms.</br>
It serves as an intermediary table that connects the wp_posts table (or other content-related tables) and the wp_terms table, allowing for the association of content items with specific taxonomy terms.

The fields that are created into the table are:</br>
<ins>object_id</ins>: The ID of the content item (e.g., post, page) that is associated with a taxonomy term.</br>
<ins>term_taxonomy_id</ins>: The ID of the taxonomy term to which the content item is associated.</br>
<ins>term_order</ins>: An optional field used for ordering terms within a content item.</br>

### Relations to other tables:</br>
object_id column in wp_term_relationships references the primary key (ID) column in the wp_posts table or other content-related tables, establishing a relationship between content items and taxonomy terms.
term_taxonomy_id column in wp_term_relationships references the term_taxonomy_id column in the wp_term_taxonomy table, connecting the relationship to the specific taxonomy term.
The wp_term_relationships table enables many-to-many relationships between content items and taxonomy terms.</br>
This means that a single content item can be associated with multiple taxonomy terms, and a single taxonomy term can be associated with multiple content items.</br>

![10](https://github.com/InkiStark/Wordpress-DB-Analysis/assets/116667541/6aec0a1a-4302-4f9b-9baa-d9c15de145af)

### Next table is wp_term_taxonomy:
Is table that stores information about the taxonomies and their associated terms.</br>
It provides the taxonomy-specific metadata for the terms stored in the wp_terms table.</br>
This table is crucial for managing and organizing the taxonomy system within WordPress.</br>
is primarily used to organize terms within taxonomies.</br>
It defines the hierarchical structure of the taxonomy, such as parent-child relationships between terms. </br>
This information is used to display and navigate terms in hierarchical taxonomies like categories.

The fields that are created into the table are:</br>
<ins>term_taxonomy_id</ins>: A unique identifier for each term taxonomy entry.</br>
<ins>term_id</ins>: The ID of the term to which the taxonomy entry belongs.</br>
<ins>taxonomy</ins>: The name of the taxonomy associated with the term.</br>
<ins>description</ins>: An optional description or explanation of the taxonomy term.</br>
<ins>parent</ins>: The parent term in the taxonomy hierarchy.</br>
<ins>count</ins>: The count of how many objects (e.g., posts) are associated with the term.</br>

### Relations to other tables:</br>
term_id column in wp_term_taxonomy references the term_id column in the wp_terms table. </br>
This establishes a relationship between the term and its associated term taxonomy.
Τhe wp_term_taxonomy table facilitates the relationship between terms, taxonomy, and content, </br>
it primarily operates as an intermediary table connecting terms in the wp_terms table to taxonomy-specific metadata and relationships.</br>
Therefore, the primary relationship between wp_term_taxonomy and other tables is a one-to-many relationship.</br>

![11](https://github.com/InkiStark/Wordpress-DB-Analysis/assets/116667541/61ae763e-8c96-44d5-aa84-3832fb3b7f57)

### Next table is wp_usermeta:
This table stores additional metadata or custom fields associated with user accounts.</br>
It allows you to store and retrieve extra information about users beyond the default fields provided by WordPress.</br>
is commonly used to store custom fields or additional information for users.</br>
These custom fields can hold any type of data, such as user preferences, user roles, social media profiles, or any other relevant details specific to users.

The fields that are created into the table are:</br>
<ins>umeta_id</ins>: A unique identifier for each user meta entry.</br>
<ins>user_id</ins>: The ID of the user to which the meta data belongs.</br>
<ins>meta_key</ins>: The key or name of the meta data.</br>
<ins>meta_value</ins>: The value associated with the meta data key.</br>

### Relations to other tables:</br>
The wp_usermeta table is related to the wp_users table through the user_id column, which serves as a foreign key.</br>
The user_id column in wp_usermeta corresponds to the ID column in wp_users, establishing a relationship between users and their associated metadata.</br>
Plugins or themes may establish additional relationships between the wp_usermeta table and other tables based on their specific functionality and requirements.
he relationship between the wp_usermeta and wp_users tables is a one-to-many relationship because one user can have multiple metadata entries in the wp_usermeta table,</br>
but each metadata entry corresponds to only one user in the wp_users table.

![12](https://github.com/InkiStark/Wordpress-DB-Analysis/assets/116667541/97eac9e6-74c3-4692-8bbb-ad47c3719a5a)

### Next and final table is wp_users:
This table stores information about user accounts. It is one of the fundamental tables in WordPress, responsible for managing user authentication, permissions, and basic user profile details.
The table is used to manage user accounts within WordPress. It stores essential information such as usernames, passwords, email addresses, and other user-specific details.</br>
The wp_users table is crucial for user authentication. </br>
When users log in to the WordPress site, their credentials (username and password) are matched against the information stored in this table to grant access to the appropriate user account.</br>
It serves as the foundation for user profiles. It stores basic user information like display names and contact details. Additional user metadata or custom fields can be stored in the wp_usermeta table.

The fields that are created into the table are:</br>
<ins>ID</ins>: A unique identifier for each user.</br>
<ins>user_login</ins>: The username or login name of the user.</br>
<ins>user_pass</ins>: The hashed password of the user.</br>
<ins>user_nicename</ins>: A user-friendly name or nickname for the user.</br>
<ins>user_email</ins>: The email address associated with the user.</br>
<ins>user_url</ins>: The URL or website associated with the user.</br>
<ins>user_registered</ins>: The date and time when the user account was registered.</br>
<ins>user_activation_key</ins>: An activation key used for user account activation (optional).</br>
<ins>user_status</ins>: The status of the user account.</br>
<ins>display_name</ins>: The display name of the user.</br>

### Relations to other tables:</br>
User-specific metadata or custom fields are stored in the wp_usermeta table. </br>
The ID column in the wp_users table serves as a primary key, and it is referenced as a foreign key (user_id) in the wp_usermeta table.</br>
Users are associated with the content they create, such as posts or pages, through the post_author column in the wp_posts table.</br>
The ID column in the wp_users table is referenced as a foreign key in the wp_posts table to link authors with their content.</br>
The relationship between the wp_users table and other tables in WordPress is a one-to-many relationship.

![13](https://github.com/InkiStark/Wordpress-DB-Analysis/assets/116667541/048513ae-ad89-4139-9991-0bfa23de77fd)
