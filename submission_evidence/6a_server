"""Flask server for the emotion detector."""

from flask import Flask, request

from EmotionDetection import emotion_detector


app = Flask(__name__)


@app.route("/")
def home():
    """Show a simple page for testing the application."""
    return """
    <html>
        <head><title>Emotion Detector</title></head>
        <body>
            <h1>Emotion Detector</h1>
            <form action="/emotionDetector">
                <input type="text" name="textToAnalyze">
                <input type="submit" value="Analyze">
            </form>
        </body>
    </html>
    """


@app.route("/emotionDetector")
def emotion_detector_route():
    """Analyze the text passed in the query string."""
    text_to_analyze = request.args.get("textToAnalyze")
    response = emotion_detector(text_to_analyze)

    return (
        "For the given statement, the system response is "
        f"'anger': {response['anger']}, "
        f"'disgust': {response['disgust']}, "
        f"'fear': {response['fear']}, "
        f"'joy': {response['joy']} and "
        f"'sadness': {response['sadness']}. "
        f"The dominant emotion is {response['dominant_emotion']}."
    )


if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)
