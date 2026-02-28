from flask import Flask, render_template

app = Flask(__name__)

@app.route('/')
def home():
    # Centralized place to manage your links
    profile_data = {
        "name": "Your Name",
        "bio": "Creator | Developer | Coffee Enthusiast",
        "social_links": [
            {"platform": "Instagram", "url": "https://instagram.com/yourhandle", "color": "#E4405F"},
            {"platform": "Twitter / X", "url": "https://twitter.com/yourhandle", "color": "#1DA1F2"},
            {"platform": "GitHub", "url": "https://github.com/yourhandle", "color": "#333"},
            {"platform": "LinkedIn", "url": "https://linkedin.com/in/yourhandle", "color": "#0077B5"},
            {"platform": "Portfolio", "url": "https://yourwebsite.com", "color": "#2ecc71"}
        ]
    }
    return render_template('index.html', user=profile_data)

if __name__ == '__main__':
    app.run(debug=True)

    <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{{ user.name }} | Links</title>
    <style>
        body {
            font-family: 'Segoe UI', sans-serif;
            background-color: #f4f4f9;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            margin: 0;
        }
        .container {
            text-align: center;
            width: 100%;
            max-width: 400px;
            padding: 20px;
        }
        .profile-pic {
            width: 100px;
            height: 100px;
            background: #ccc;
            border-radius: 50%;
            margin-bottom: 15px;
        }
        h1 { margin-bottom: 5px; font-size: 24px; }
        p { color: #666; margin-bottom: 30px; }
        .link-card {
            display: block;
            padding: 15px;
            margin-bottom: 15px;
            text-decoration: none;
            color: white;
            font-weight: bold;
            border-radius: 8px;
            transition: transform 0.2s;
        }
        .link-card:hover {
            transform: scale(1.03);
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>{{ user.name }}</h1>
        <p>{{ user.bio }}</p>

        {% for link in user.social_links %}
        <a href="{{ link.url }}" class="link-card" style="background-color: {{ link.color }};">
            {{ link.platform }}
        </a>
        {% endfor %}
    </div>
</body>
</html>
