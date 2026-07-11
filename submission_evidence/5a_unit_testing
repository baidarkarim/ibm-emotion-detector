"""Unit tests for the emotion detector."""

import unittest
from unittest.mock import Mock, patch

from EmotionDetection.emotion_detection import emotion_detector


def mock_response(dominant_emotion):
    """Create a Watson-style mock response."""
    scores = {
        "anger": 0.01,
        "disgust": 0.01,
        "fear": 0.01,
        "joy": 0.01,
        "sadness": 0.01,
    }
    scores[dominant_emotion] = 0.90
    return Mock(json=lambda: {"emotionPredictions": [{"emotion": scores}]})


class TestEmotionDetector(unittest.TestCase):
    """Test expected dominant emotions."""

    @patch("EmotionDetection.emotion_detection.requests.post")
    def test_joy(self, mock_post):
        mock_post.return_value = mock_response("joy")
        result = emotion_detector("I am glad this happened.")
        self.assertEqual(result["dominant_emotion"], "joy")

    @patch("EmotionDetection.emotion_detection.requests.post")
    def test_anger(self, mock_post):
        mock_post.return_value = mock_response("anger")
        result = emotion_detector("I am really mad about this.")
        self.assertEqual(result["dominant_emotion"], "anger")

    @patch("EmotionDetection.emotion_detection.requests.post")
    def test_disgust(self, mock_post):
        mock_post.return_value = mock_response("disgust")
        result = emotion_detector("I feel disgusted by this situation.")
        self.assertEqual(result["dominant_emotion"], "disgust")

    @patch("EmotionDetection.emotion_detection.requests.post")
    def test_sadness(self, mock_post):
        mock_post.return_value = mock_response("sadness")
        result = emotion_detector("I feel very sad today.")
        self.assertEqual(result["dominant_emotion"], "sadness")

    @patch("EmotionDetection.emotion_detection.requests.post")
    def test_fear(self, mock_post):
        mock_post.return_value = mock_response("fear")
        result = emotion_detector("I am afraid this could go wrong.")
        self.assertEqual(result["dominant_emotion"], "fear")


if __name__ == "__main__":
    unittest.main()
