Two Tables Design Recipe Template

Copy this recipe template to design and create two related database tables from a specification.

1. Extract nouns from the user stories or specification

# EXAMPLE USER STORY:
# (analyse only the relevant part - here the final line).

As a blogger
So I can write interesting stuff
I want to write posts having a title.

As a blogger
So I can write interesting stuff
I want to write posts having a content.

As a blogger
So I can let people comment on interesting stuff
I want to allow comments on my posts.

As a blogger
So I can let people comment on interesting stuff
I want the comments to have a content.

As a blogger
So I can let people comment on interesting stuff
I want the author to include their name in comments.

Nouns:
posts, post title, post content, comments, comment content, commenter name

2. Infer the Table Name and Columns

Record - Properties
posts -	title, content
comments - commenter_name, contents

Name of the first table (always plural): posts

Column names: title, content

Name of the second table (always plural): comments

Column names: commenter_name, content

3. Decide the column types.

Table: posts
id: SERIAL
title: text
content: text

Table: comments
id: SERIAL
commenter_name: text
content: text

4. Decide on The Tables Relationship

Can one [POSTS] have many [COMMENTS]? YES
Can one [COMMENTS] have many [POSTS]? NO
You'll then be able to say that:

[POSTS] has many [COMMENTS]
And on the other side, [COMMENTS] belongs to [POSTS]
In that case, the foreign key is in the table [B]

4. Write the SQL.

-- file: comments_table.sql

CREATE TABLE posts (
  id SERIAL PRIMARY KEY,
  title text,
  content text
);

CREATE TABLE comments (
  id SERIAL PRIMARY KEY,
  commenter_name text,
  content text,
  post_id int,
  constraint fk_posts foreign key(post_id)
    references posts(id)
    on delete cascade
);

5. Create the tables.

psql -h 127.0.0.1 database_name < albums_table.sql
