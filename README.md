# Blog-Project
Blog Project_using python and django with API

# 📃 Blog Project: Assignment Summary & Documentation

✅ Assignment Requirements:
User Authentication

Implemented JWT-based login and registration using Django REST Framework.

Used SimpleJWT for generating access and refresh tokens.

Login/Register available via both frontend and Postman.

Blog Management (CRUD APIs)

Created APIs for:

✅ Listing blog posts (with pagination of 10 per page)

✅ Creating a blog post

✅ Updating and deleting (only by the blog's author)

✅ Getting blog details

Used APIView and GenericAPIView (like ListCreateAPIView, RetrieveUpdateDestroyAPIView).

Pagination

Implemented via DRF settings:

python
Copy
Edit
REST_FRAMEWORK = {
    'DEFAULT_PAGINATION_CLASS': 'rest_framework.pagination.PageNumberPagination',
    'PAGE_SIZE': 10
}
Likes and Comments

Users can like a post once.

Comments are associated with a blog post and user.

All handled via DRF views and displayed on the frontend.

Frontend (index.html)

Designed using Bootstrap.

Shows:

Blog post title, content preview, author, date-

user http://127.0.0.1:8000/
![image](https://github.com/user-attachments/assets/beadca7c-9980-4b25-bf2a-4e1da0e8a0f5)


❤️ Like, 🔗 Share, 💬 Comment box

Logged-in user displayed on top-left corner

🔽 Load More button for pagination (2 posts/page for testing, can change to 10)

📌 API Endpoints Summary
Endpoint	Method	Description
/api/token/	POST	Login to get JWT tokens
http://127.0.0.1:8000/api/token/
![image](https://github.com/user-attachments/assets/0b34cb66-28cb-4a76-aecc-0ae0a9a950d6)


/api/register/	POST	Register a new user
http://127.0.0.1:8000/api/register/
/api/posts/	GET	Get list of blog posts (paginated)
http://127.0.0.1:8000/api/posts/

/api/posts/	POST	Create a new blog post
/api/posts/<id>/	GET	Retrieve a blog post
/api/posts/<id>/	PUT	Update a blog post
/api/posts/<id>/	DELETE	Delete a blog post

http://127.0.0.1:8000/api/posts/1/
/api/posts/<id>/like/	POST	Like/unlike a post
/api/posts/<id>/comments/	GET	Get all comments of a post
/api/posts/<id>/comments/	POST	Add a comment to a post

🧪 How to Test in Postman
1. Register
Endpoint: POST /api/register/

Body:

json
Copy
Edit
{
  "username": "admin",
  "password": "admin"
}
2. Login
Endpoint: POST /api/token/

Body:

json
Copy
Edit
{
  "username": "neetu",
  "password": "password123"
}
Save access token and use in headers as:

pgsql
Copy
Edit
Authorization: Bearer <access-token>
3. Create Blog
Endpoint: POST /api/posts/

Headers: Authorization: Bearer <token>
![image](https://github.com/user-attachments/assets/c6044d45-debb-423f-8f75-4d27a2f8adbe)


Body:

json
Copy
Edit
{
  "title": "My Blog",
  "content": "This is a great blog!",
  "status": "published"
}
4. Like Post
Endpoint: POST /api/posts/<id>/like/

Headers: same as above

5. Add Comment
Endpoint: POST /api/posts/<id>/comments/

Body:

json
Copy
Edit
{ "content": "Nice blog!" }
💡 Where Each Feature is Implemented:
User Register/Login: views.py > RegisterView, /api/token/

Blog CRUD:

List/Create: BlogPostListCreateView
![image](https://github.com/user-attachments/assets/1940b19e-1f1e-47c2-87cb-f7533fb8493e)



Retrieve/Update/Delete: BlogPostRetrieveUpdateDestroyView

Likes: toggle_like view

Comments: CommentListCreateView

Pagination: applied via DRF settings

Frontend:

Login: login.html

Blog Display: index.html with JS for fetch, like, comment,post




