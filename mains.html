<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Shadow Chat</title>
    <style>
        body {
            background: radial-gradient(circle, rgba(0,0,0,1) 0%, rgba(0,0,0,1) 50%, rgba(0,0,0,0.7) 100%);
            color: white;
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            animation: fadeIn 1s ease forwards; /* Fade-in animation */
        }
        @keyframes fadeIn {
            from {
                opacity: 0;
                transform: translateY(-50px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
        @keyframes expandBackground {
            0% {
                background-size: 100% 100%;
            }
            100% {
                background-size: 150% 150%;
            }
        }
        #content {
            width: 80%;
            max-width: 600px;
            text-align: center; /* Center align content */
            opacity: 0; /* Initially hidden */
            animation: fadeInContent 1s ease forwards; /* Fade-in animation for content */
        }
        @keyframes fadeInContent {
            from {
                opacity: 0;
            }
            to {
                opacity: 1;
            }
        }
        #postContainer {
            max-height: 60vh; /* Adjust as needed */
            overflow-y: auto; /* Enable vertical scrolling */
        }
        .post {
            background-color: black;
            padding: 10px;
            margin-bottom: 10px;
            border-radius: 5px;
            box-shadow: 0 0 10px rgba(255, 255, 255, 0.5);
            border: 2px solid transparent; /* Add border */
            transition: border-color 0.3s ease; /* Add transition for glow effect */
        }
        .post:hover {
            border-color: white; /* Glow effect on hover */
        }
        .reply {
            background-color: #333;
            color: white;
            padding: 5px;
            margin-top: 5px;
            border-radius: 5px;
        }
        .thumbs {
            display: inline-block;
            margin-left: 10px;
            cursor: pointer;
            color: white;
        }
        #clearStorage {
            position: fixed;
            top: 10px;
            right: 10px;
            padding: 10px 20px;
            border: 2px solid transparent;
            border-radius: 5px;
            background-color: black;
            color: white;
            cursor: pointer;
            transition: border-color 0.3s ease, box-shadow 0.3s ease;
        }
        #clearStorage:hover {
            border-color: white;
            box-shadow: 0 0 10px white;
        }
        #adminButton {
            position: fixed;
            top: 10px;
            left: 10px;
            padding: 10px 20px;
            border: 2px solid transparent;
            border-radius: 5px;
            background-color: black;
            color: white;
            cursor: pointer;
            transition: border-color 0.3s ease, box-shadow 0.3s ease;
        }
        #adminButton:hover {
            border-color: white;
            box-shadow: 0 0 10px white;
        }
        .sparkle {
            position: absolute;
            pointer-events: none;
            width: 20px;
            height: 20px;
            border-radius: 50%;
            background-color: transparent;
            border: 2px solid white;
            animation: sparkleAnim 1s linear;
        }
        @keyframes sparkleAnim {
            0% {
                opacity: 1;
                transform: scale(0);
            }
            100% {
                opacity: 0;
                transform: scale(1);
            }
        }
    </style>
</head>
<body>
    <div id="content">
        <h1>Shadow Chat</h1>

        <!-- Form for sending posts -->
        <form id="postForm">
            <textarea id="postContent" rows="4" cols="50" placeholder="Write your post..." required></textarea><br>
            <button type="submit">Post</button>
        </form>

        <!-- Clear storage button with password prompt -->
        <button id="clearStorage">Clear Storage</button>

        <!-- Admin button with password protection -->
        <button id="adminButton">Admin</button>

        <!-- Displaying posts -->
        <div id="postContainer"></div>
    </div>

    <script>
        let posts = JSON.parse(localStorage.getItem('posts')) || [];
        let showNames = false; // Initially set to false to hide names

        // Ask for user's name and store it in local storage
        let username = localStorage.getItem('username');
        if (!username) {
            username = prompt("Please enter your name:");
            localStorage.setItem('username', username);
        }

        // Welcome message
        const welcomeMessage = document.createElement("p");
        welcomeMessage.textContent = `Welcome to Shadow Chat, ${username}! Feel free to post anything you want as a shadow in the light.`;
        document.getElementById("content").insertBefore(welcomeMessage, document.getElementById("postForm"));

        function renderPosts() {
            const postContainer = document.getElementById("postContainer");
            postContainer.innerHTML = "";

            // Sort posts based on the total score (thumbs up - thumbs down)
            posts.sort((a, b) => (b.thumbsUp - b.thumbsDown) - (a.thumbsUp - a.thumbsDown));

            posts.forEach((post, index) => {
                const postElement = document.createElement("div");
                postElement.classList.add("post");
                const userNameDisplay = showNames ? `<strong>${post.username}: </strong>` : '';
                postElement.innerHTML = `<p>${userNameDisplay}${formatText(post.content)}</p><span class="thumbs" onclick="thumbsUp(${index})">👍 ${post.thumbsUp}</span><span class="thumbs" onclick="thumbsDown(${index})">👎 ${post.thumbsDown}</span>`;

                // Add event listener to track cursor movement for sparkle effect
                postElement.addEventListener("mousemove", function(event) {
                    createSparkle(event.clientX, event.clientY);
                });

                // Reply form for each post
                const replyForm = document.createElement("form");
                replyForm.innerHTML = `<textarea id="replyContent_${index}" rows="2" cols="30" placeholder="Write a reply..." required></textarea><br><button type="submit">Reply</button>`;
                replyForm.addEventListener("submit", function(event) {
                    event.preventDefault();
                    const replyContent = document.getElementById(`replyContent_${index}`).value.trim();
                    if (replyContent !== "") {
                        addReply(index, replyContent);
                        document.getElementById(`replyContent_${index}`).value = "";
                    }
                });
                postElement.appendChild(replyForm);

                // Display replies
                if (post.replies.length > 0) {
                    const repliesContainer = document.createElement("div");
                    post.replies.forEach(reply => {
                        const replyElement = document.createElement("div");
                        replyElement.classList.add("reply");
                        replyElement.innerHTML = `<p>${formatText(reply)}</p>`;
                        repliesContainer.appendChild(replyElement);
                    });
                    postElement.appendChild(repliesContainer);
                }

                postContainer.appendChild(postElement);
            });
        }

        // Function to format long text into paragraphs
        function formatText(text) {
            const maxLength = 40; // Maximum characters per line
            const words = text.split(' ');
            let formattedText = '';
            let line = '';
            for (let i = 0; i < words.length; i++) {
                if ((line + words[i]).length > maxLength) {
                    formattedText += `<p>${line}</p>`;
                    line = '';
                }
                line += words[i] + ' ';
            }
            if (line !== '') {
                formattedText += `<p>${line}</p>`;
            }
            return formattedText;
        }

        // Function to create sparkle effect
        document.addEventListener("mousemove", function(event) {
            const target = event.target;
            // Check if the cursor is over the post boxes or reply boxes
            if (!target.classList.contains("post") && !target.classList.contains("reply")) {
                createSparkle(event.clientX, event.clientY);
            }
        });

        function createSparkle(x, y) {
            const sparkle = document.createElement("div");
            sparkle.classList.add("sparkle");
            sparkle.style.left = `${x}px`;
            sparkle.style.top = `${y}px`;
            document.body.appendChild(sparkle);

            // Remove sparkle element after animation
            sparkle.addEventListener("animationend", function() {
                sparkle.remove();
            });
        }

        function addPost(content) {
            const newPost = {
                username: username,
                content: content,
                thumbsUp: 0,
                thumbsDown: 0,
                replies: []
            };
            posts.push(newPost);
            savePostsToLocalStorage(); // Save posts to localStorage
            renderPosts();
        }

        function addReply(postIndex, replyContent) {
            const post = posts[postIndex];
            if (post) {
                post.replies.push(replyContent);
                savePostsToLocalStorage(); // Save posts to localStorage
                renderPosts();
            }
        }

        function thumbsUp(index) {
            const post = posts[index];
            if (post) {
                post.thumbsUp++;
                savePostsToLocalStorage(); // Save posts to localStorage
                renderPosts();
            }
        }

        function thumbsDown(index) {
            const post = posts[index];
            if (post) {
                post.thumbsDown++;
                savePostsToLocalStorage(); // Save posts to localStorage
                renderPosts();
            }
        }

        function savePostsToLocalStorage() {
            localStorage.setItem('posts', JSON.stringify(posts));
        }

        document.getElementById("postForm").addEventListener("submit", function(event) {
            event.preventDefault();
            const postContent = document.getElementById("postContent").value.trim();
            if (postContent !== "") {
                addPost(postContent);
                document.getElementById("postContent").value = "";
            }
        });

        document.getElementById("clearStorage").addEventListener("click", function() {
            const password = prompt("Enter password to clear storage:");
            if (password === "ShadowGod101") {
                localStorage.clear();
                posts = [];
                renderPosts();
            } else {
                alert("Incorrect password!");
            }
        });

        document.getElementById("adminButton").addEventListener("click", function() {
            const password = prompt("Enter password to access admin options:");
            if (password === "ShadowGod101") {
                const options = ["Display Names", "Hide Names"];
                const choice = prompt("Select an option:\n1. Display Names\n2. Hide Names");
                if (choice === "1") {
                    showNames = true;
                } else if (choice === "2") {
                    showNames = false;
                }
                renderPosts();
            } else {
                alert("Incorrect password!");
            }
        });

        // Initially render posts when page loads
        renderPosts();

        // Show content after animation
        document.getElementById("content").style.opacity = "1";
    </script>
</body>
</html>
