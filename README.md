# kilimani-site.txt
my mp 3 downloader app
import youtube_dl

def download_youtube_mp3(url, output_path):
    try:
        ydl_opts = {
            'format': 'bestaudio/best',
            'outtmpl': output_path + '.%(ext)s',
            'postprocessors': [{
                'key': 'FFmpegExtractAudio',
                'preferredcodec': 'mp3',
                'preferredquality': '192',
            }],
            'verbose': True  # Enable verbose output
        }

        with youtube_dl.YoutubeDL(ydl_opts) as ydl:
            ydl.download([url])

        print("MP3 downloaded successfully!")
    except Exception as e:
        print(f"Error: {e}")

# Example usage
video_url = "https://www.youtube.com/watch?v=dQw4w9WgXcQ"
output_file = "/path/to/save/audio"

download_youtube_mp3(video_url, output_file)
