import tweepy
import smtplib
from email.mime.text import MIMEText
from datetime import datetime

# Twitter Credentials
api_key = "K8h40P7faqibR1p0VcH1lQb8f"
api_secret = "bduxZg3cUdfpICPpgXN7NNMojNQcE6qdj8TqT6p9HRwm2V8g9b"
bearer_token = r"AAAAAAAAAAAAAAAAAAAAAIHhxgEAAAAAEHDmk7l7wAUXxU9HoztobnFpHv0%3Dtu5NYpmSTw12sMP2NtoFwpsPODdd9nlgANLbTVF5aPrK5BRd5u"
access_token = "1860442091848945664-3vN9KyQ4ATTVdJSxKT1smQfKTdGQG1"
access_token_secret = "X1a4QmHzqHp3etaje831P630XNZbiKieDsTCobBvWvuQF"

# Email Configuration
SMTP_SERVER = "smtp.gmail.com"
SMTP_PORT = 587
EMAIL_ADDRESS = "hubert.page01@gmail.com"
EMAIL_PASSWORD = "cfbh iqio pzho pcqq"  # Replace with your app-specific password

# Connect to Twitter API
client = tweepy.Client(bearer_token, api_key, api_secret, access_token, access_token_secret)
auth = tweepy.OAuth1UserHandler(api_key, api_secret, access_token, access_token_secret)
api = tweepy.API(auth)

# Send Tweet Function
def send_tweet(message):
    try:
        response = client.create_tweet(text=message)
        print("Tweet sent successfully:", response)
    except Exception as e:
        print(f"Error sending tweet: {e}")

# Send Email Function
def send_email(subject, body, recipient):
    try:
        msg = MIMEText(body)
        msg["Subject"] = subject
        msg["From"] = EMAIL_ADDRESS
        msg["To"] = recipient

        with smtplib.SMTP(SMTP_SERVER, SMTP_PORT) as server:
            server.starttls()
            server.login(EMAIL_ADDRESS, EMAIL_PASSWORD)
            server.sendmail(EMAIL_ADDRESS, recipient, msg.as_string())
        print("Email sent successfully.")
    except Exception as e:
        print(f"Error sending email: {e}")

# Main Function
def main():
    # Calculate the current day
    start_date = datetime(2024, 12, 24)  # Replace with your start date
    current_date = datetime.now()
    day_number = (current_date - start_date).days + 1

    # Tweet content
    tweet_message = f"Day {day_number}: Bonjour @Turo, un autre jour sans nouvelle sur la fraude de 3000€. Monsieur Genaro toujours injoignable. Répondeur immédiat 7j/7 24h/24 au 01 59 44 03 66. N'hésitez pas à raconter votre mauvaise expérience avec Turo sur le tweet épinglé  #CustomerService"
    send_tweet(tweet_message)

    # Email content
    email_subject = "Follow-Up: €3000 Fraud Claim"
    email_body = f"""\
Bonjour,

Ceci est un suivi concernant la réclamation pour une fraude de 3000 € associée à vos services. N'hésiter pas à suivre les démarches sur https://x.com/TuroSinistre
Veuillez répondre rapidement, je vous prie.

Cordialement,
Hubert
"""
    recipient = "live-inbox-turo+replyto-11030.e36bda00-f35b-4837-a863-2f6a44a1548c@origamirisk.com"
    send_email(email_subject, email_body, recipient)

# Run the main function
if __name__ == "__main__":
    main()
