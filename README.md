import datetime
import requests

class SocialMediaScheduler:
    def __init__(self):
        self.scheduled_posts = []

    def schedule_post(self, platform, content, post_time):
        try:
            # Validate inputs
            if platform not in ['Twitter', 'Facebook', 'Instagram']:
                raise ValueError("Invalid platform")
            
            post_time = datetime.datetime.strptime(post_time, "%Y-%m-%d %H:%M:%S")
            self.scheduled_posts.append({'platform': platform, 'content': content, 'post_time': post_time})
            print(f"Scheduled post on {platform} at {post_time}")
        except ValueError as e:
            print(f"Error: {e}")

    def post_now(self, platform, content):
        try:
            if platform == 'Twitter':
                # Post to Twitter using API
                pass
            elif platform == 'Facebook':
                # Post to Facebook using API
                pass
            elif platform == 'Instagram':
                # Post to Instagram using API
                pass
            print(f"Posted to {platform}: {content}")
        except Exception as e:
            print(f"Error: {e}")

    def check_scheduled_posts(self):
        now = datetime.datetime.now()
        for post in self.scheduled_posts:
            if post['post_time'] <= now:
                self.post_now(post['platform'], post['content'])
                self.scheduled_posts.remove(post)

if __name__ == "__main__":
    scheduler = SocialMediaScheduler()
    scheduler.schedule_post('Twitter', 'Hi Meghana', '2025-02-08 20:00:00')
    scheduler.check_scheduled_posts()
