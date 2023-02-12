---
layout: post
title: Datenanalyse mit Python
date: 2020-01-20
last_modified_at: 2023-02-11
cover_image: 2021-05-03-feature.jpg
author: Yongguang Lin
categories: automation
excerpt_separator: <!--more-->
---

> Photo by [Levi Stute](https://unsplash.com/@levi_stute_cinematography).

Datenanalyse ist der Prozess der Untersuchung und Modellierung von Daten, um aussagekräftige Erkenntnisse und Informationen zu gewinnen. Python ist aufgrund seiner leistungsstarken und benutzerfreundlichen Bibliotheken und Werkzeuge eine beliebte Programmiersprache für die Datenanalyse.
<!--more-->

Python ist eine vielseitige Sprache, die häufig für Automatisierungsaufgaben verwendet wird. Hier sind einige beliebte Beispiele für Automatisierungsaufgaben, die mit Python durchgeführt werden können:

- Web Scraping: Mit Python lassen sich Daten aus Websites extrahieren, die dann für verschiedene Zwecke wie Datenanalyse, Datenvisualisierung usw. verwendet werden können.

- Automatisierung von sich wiederholenden Aufgaben: Mit Python können sich wiederholende Aufgaben automatisiert werden, z. B. das Ausfüllen von Online-Formularen, das Versenden von E-Mails usw.

- Automatisieren von Dateioperationen: Mit Python lassen sich verschiedene Dateioperationen automatisieren, z. B. das Umbenennen von Dateien, das Verschieben von Dateien von einem Ort zum anderen usw.

- Automatisierung der Bildverarbeitung: Python kann zur Automatisierung von Bildverarbeitungsaufgaben verwendet werden, z. B. zur Größenänderung von Bildern, zur Konvertierung von Bildern in verschiedene Formate usw.

- Automatisierung der Datenverarbeitung: Python kann zur Automatisierung von Datenverarbeitungsaufgaben verwendet werden, z. B. zur Bereinigung von Daten, zur Umwandlung von Daten, zur Aggregation von Daten usw.

- Automatisierung von Systemverwaltungsaufgaben: Mit Python lassen sich verschiedene Aufgaben der Systemverwaltung automatisieren, z. B. die Verwaltung von Servern, Datenbanken usw.

- Automatisierung von wissenschaftlichen Berechnungen: Python ist in der wissenschaftlichen Datenverarbeitung weit verbreitet und kann zur Automatisierung verschiedener wissenschaftlicher Berechnungen wie numerischer Simulationen, Datenanalysen usw. verwendet werden.

Dies sind nur einige Beispiele für die vielen Automatisierungsaufgaben, die mit Python erledigt werden können. Die Einfachheit der Sprache, ihre Vielseitigkeit und die große Gemeinschaft von Entwicklern machen sie zur idealen Wahl für Automatisierungsaufgaben.

# Web Scraping
Beim Web Scraping werden automatisch Daten aus Websites extrahiert. Dabei werden HTTP-Anfragen an den Server einer Website gesendet, der HTML-Inhalt der Seiten heruntergeladen und dann analysiert, um die Daten zu extrahieren, an denen Sie interessiert sind.

Web Scraping wird häufig für verschiedene Zwecke eingesetzt, z. B:

- Datenerfassung für Forschung oder Analyse
- Preisvergleiche und Marktforschung
- Scraping von Stellenangeboten oder Immobilienangeboten
- Sammeln von Kontaktinformationen für Marketingzwecke

Es gibt viele Tools und Bibliotheken für Web Scraping in verschiedenen Programmiersprachen, einschließlich Python. Zu den beliebtesten Bibliotheken für Web Scraping in Python gehören BeautifulSoup, Scrapy und Selenium.

### BeautifulSoup 
```python
import requests
from bs4 import BeautifulSoup

# Make a request to the website
url = "https://www.example.com"
response = requests.get(url)

# Check if the request was successful
if response.status_code == 200:
    # Parse the HTML content of the page
    soup = BeautifulSoup(response.text, "html.parser")

    # Find the data you want to scrape
    title = soup.find("title").text
    body = soup.find("body").text

    # Print the data
    print("Title:", title)
    print("Body:", body)
else:
    print("Request failed with status code", response.status_code)
```
In diesem Beispiel verwenden wir zunächst die requests-Bibliothek, um eine Anfrage an die Website zu stellen. Dann verwenden wir die BeautifulSoup-Bibliothek, um den HTML-Inhalt der Seite zu analysieren und die Daten zu finden, die wir auslesen wollen.

In diesem Fall suchen wir die Elemente title und body der Seite und geben deren Inhalt aus.

Beachten Sie, dass dies nur ein einfaches Beispiel ist und dass Sie den Code je nach der Struktur der Website, die Sie auslesen wollen, möglicherweise ändern müssen. Außerdem ist es wichtig, die Nutzungsbedingungen von Websites zu respektieren und das Scraping von Websites zu vermeiden, die dies nicht zulassen.

### Scrapy
Scrapy ist ein beliebtes und leistungsstarkes Open-Source-Framework für Web-Scraping in Python. Es bietet eine benutzerfreundliche API zum Extrahieren von Daten aus Websites und verfügt über eine Reihe integrierter Funktionen, die es für groß angelegte Web-Scraping-Projekte gut geeignet machen.

Hier ein einfaches Beispiel dafür, wie Sie Scrapy zum Scrapen einer Website verwenden können:
```python
import scrapy

class MySpider(scrapy.Spider):
    name = "myspider"
    start_urls = [
        'https://www.example.com/page1',
        'https://www.example.com/page2',
    ]

    def parse(self, response):
        for quote in response.css('div.quote'):
            yield {
                'text': quote.css('span.text::text').get(),
                'author': quote.css('span small::text').get(),
                'tags': quote.css('div.tags a.tag::text').getall(),
}
```
In diesem Beispiel definieren wir eine Scrapy-Spider-Klasse namens MySpider, die die start_urls und die parse-Methode angibt. Die start_urls definieren die URLs, mit denen der Spider startet, und die parse-Methode wird für jede Antwort aufgerufen, die der Spider erhält.

Die parse-Methode verwendet CSS-Selektoren, um Daten aus der HTML-Antwort zu extrahieren, und gibt ein Wörterbuch mit den extrahierten Daten zurück.

Sie können den Spider mit dem folgenden Befehl starten:
```
scrapy runspider myspider.py
```
Dadurch wird der Spider gestartet und die Daten von den angegebenen URLs abgerufen. Die extrahierten Daten werden auf der Konsole ausgegeben, aber Sie können sie auch in einer Datei speichern oder in einer Datenbank zur späteren Verwendung ablegen.

Scrapy bietet viele weitere Funktionen und Optionen, darunter:

- Unterstützung für das Verfolgen von Links zu anderen Seiten
- Unterstützung für die Handhabung von Weiterleitungen, Cookies und Authentifizierung
- Integrierte Unterstützung für den Umgang mit gängigen Web-Scraping-Problemen, wie z.B. Ratenbegrenzung und Umgang mit defekten Links
- Unterstützung für das Speichern von gescrapten Daten in verschiedenen Formaten, einschließlich CSV, JSON und XML

Weitere Informationen über Scrapy und seine Funktionen finden Sie in der offiziellen Dokumentation.
### Selenium
Unter Web Scraping versteht man das Extrahieren von Daten aus Websites. Selenium ist ein beliebtes Tool zur Automatisierung von Webbrowsern und eignet sich daher hervorragend für Web Scraping. Mit Selenium können Sie Skripte schreiben, um einen Browser zu automatisieren und mit Websites zu interagieren, genau wie Sie es manuell tun würden. Auf diese Weise können Sie Daten von Websites extrahieren, die dynamisch generiert werden, z. B. solche, die JavaScript zum Laden von Inhalten verwenden.
```python
from selenium import webdriver

# Create a web driver
driver = webdriver.Firefox()

# Navigate to a website
url = "https://www.example.com"
driver.get(url)

# Extract the title of the website
title = driver.title

# Print the title
print(title)

# Close the web driver
driver.quit()
```
In diesem Beispiel importieren wir zunächst das Webdriver-Modul aus dem Selenium-Paket. Dann erstellen wir einen Webtreiber mit der Firefox-Klasse. Wir verwenden die get-Methode, um zu einer Website zu navigieren, und die title-Eigenschaft, um den Titel zu extrahieren. Schließlich drucken wir den Titel aus und schließen den Webtreiber mit der quit-Methode.

Dies ist nur ein einfaches Beispiel, und es gibt noch viel mehr, was Sie mit Selenium machen können. Sie können es zum Beispiel verwenden, um mit Elementen auf einer Seite zu interagieren, wie Schaltflächen, Links und Formularen, und Daten aus ihnen zu extrahieren. Sie können mit Selenium auch komplexe Operationen durchführen, wie das Ausfüllen von Formularen und das Klicken durch mehrere Seiten, um Daten zu extrahieren. Der Schlüssel zum erfolgreichen Web Scraping mit Selenium ist das Verständnis der Struktur der zu scannenden Websites und der Elemente, mit denen Sie interagieren müssen.
# Versenden von E-Mails
Sie können die smtplib-Bibliothek in Python verwenden, um E-Mails zu versenden. Hier ist ein Beispiel, das zeigt, wie man eine einfache Text-E-Mail versendet:
### Google Mail
```python
import smtplib

# Gmail account credentials
gmail_user = "your_email@gmail.com"
gmail_password = "your_password"

# Email recipient
to = "recipient_email@example.com"

# Email content
subject = "Test email from Python"
body = "This is a test email sent from Python."
email_text = f"Subject: {subject}\n\n{body}"

# Connect to the Gmail SMTP server
server = smtplib.SMTP_SSL("smtp.gmail.com", 465)
server.login(gmail_user, gmail_password)

# Send the email
server.sendmail(gmail_user, to, email_text)

# Close the SMTP connection
server.quit()

```
In diesem Beispiel importieren wir zunächst die smtplib-Bibliothek, die Funktionen zum Senden von E-Mails bereitstellt. Dann geben wir die Anmeldedaten für das Gmail-Konto und den E-Mail-Empfänger an.

Anschließend erstellen wir den E-Mail-Inhalt, der einen Betreff und einen Text enthält. Anschließend stellen wir mit der Funktion SMTP_SSL, die eine sichere SSL-Verbindung herstellt, eine Verbindung zum SMTP-Server von Google Mail her.

Anschließend melden wir uns mit der Login-Methode beim Gmail-Konto an und senden die E-Mail mit der Sendmail-Methode. Schließlich wird die SMTP-Verbindung mit der quit-Methode geschlossen.

Beachten Sie, dass es aus Sicherheitsgründen nicht empfehlenswert ist, Ihr Passwort im Klartext in Ihrem Code zu speichern. Stattdessen können Sie es in einer Umgebungsvariablen oder einer Konfigurationsdatei speichern und von dort abrufen.
### Outlook
Sie können die smtplib-Bibliothek in Python verwenden, um eine E-Mail über Hotmail (jetzt Outlook genannt) zu versenden. Hier ist ein Beispiel dafür, wie Sie eine einfache E-Mail senden können:
```python
import smtplib

# Connect to the Hotmail server
server = smtplib.SMTP("smtp-mail.outlook.com", 587)
server.ehlo()
server.starttls()
server.ehlo()

# Login to your Hotmail account
username = "your_email@hotmail.com"
password = "your_password"
server.login(username, password)

# Send the email
from_address = "your_email@hotmail.com"
to_address = "recipient_email@example.com"
subject = "Test Email from Python"
body = "This is a test email sent from Python using the smtplib library."
message = f"Subject: {subject}\n\n{body}"
server.sendmail(from_address, to_address, message)

# Logout from the server
server.quit()
```
In diesem Beispiel stellen wir zunächst eine Verbindung zum Hotmail-Server her, indem wir die SMTP-Klasse aus der smtplib-Bibliothek verwenden. Dann melden wir uns mit der Methode login bei Ihrem Hotmail-Konto an und senden die E-Mail mit der Methode sendmail. Schließlich melden wir uns mit der quit-Methode vom Server ab.

Beachten Sie, dass Sie die Variablen username und password durch die E-Mail-Adresse und das Passwort Ihres Hotmail-Kontos ersetzen müssen und die Variable to_address durch die E-Mail-Adresse des Empfängers.

Dies ist nur ein einfaches Beispiel, und es gibt viele andere Dinge, die Sie mit der smtplib-Bibliothek tun können, wie das Senden von HTML-formatierten E-Mails, das Anhängen von Dateien, usw. Weitere Informationen über die Bibliothek und ihre Funktionen finden Sie in der Python-Dokumentation.

# Automatisieren von Dateioperationen
### Umbenennen von Dateien
Hier ein Beispiel dafür, wie Sie mit Python mehrere Dateien in einem Verzeichnis umbenennen können:
```python
import os

# Path to the directory containing the files
directory = "path/to/directory"

# Loop through all files in the directory
for filename in os.listdir(directory):
    # Construct the old and new file paths
    old_file_path = os.path.join(directory, filename)
    new_file_path = os.path.join(directory, filename.replace("old", "new"))
    
    # Rename the file
    os.rename(old_file_path, new_file_path)
```
### Dateien verschieben
In Python kannst du die shutil Bibliothek verwenden, um Dateien zu verschieben. Hier ist ein Beispiel:
```python
import shutil

# Quelldatei
src_file = "original.txt"

# Zielordner
dst_folder = "destination"

# Zieldatei
dst_file = f"{dst_folder}/new.txt"

# Verschieben der Datei
shutil.move(src_file, dst_file)
```
In diesem Beispiel verwenden wir die shutil.move Funktion, um die Quelldatei original.txt in den Zielordner destination zu verschieben und dabei ihren Namen in new.txt zu ändern.

Wenn das Ziel eine bereits existierende Datei mit demselben Namen ist, wird die alte Datei überschrieben. Wenn das Ziel ein Ordner ist, wird die Quelldatei in den Ordner verschoben und behält ihren ursprünglichen Namen bei.

### Datei/Ordner löschen
In Python kannst du eine Datei oder einen Ordner löschen, indem du die os Bibliothek verwendest. Hier ist ein Beispiel:
```python
import os

# Pfad zur Datei
file_path = "path/to/file.txt"

# The path of the directory you want to delete
folder_path = "path/to/folder"

# Use the `rmdir` function to delete the directory
os.rmdir(folder_path)

# Datei löschen
os.remove(file_path)
```
### Dateien einlesen
```python
import PyPDF2

# Open the PDF file
pdf_file = open("file.pdf", "rb")

# Create a PDF reader object
pdf_reader = PyPDF2.PdfFileReader(pdf_file)

# Get the number of pages in the PDF
num_pages = pdf_reader.numPages

# Read each page of the PDF
for page_num in range(num_pages):
    page = pdf_reader.getPage(page_num)
    print(page.extractText())

# Close the PDF file
pdf_file.close()
```
```python
import docx

# Load the Word document
document = docx.Document("file.docx")

# Iterate over the paragraphs in the document
for paragraph in document.paragraphs:
    print(paragraph.text)
```
In diesem Beispiel importieren wir zunächst die python-docx-Bibliothek, die Funktionen zum Lesen und Schreiben von Word-Dokumenten bereitstellt. Dann laden wir ein Word-Dokument mit der Document-Funktion und durchlaufen die Absätze des Dokuments mit einer for-Schleife.

Für jeden Absatz verwenden wir die Eigenschaft text, um auf den Text des Absatzes zuzugreifen, den wir dann auf der Konsole ausgeben.

Beachten Sie, dass dies nur ein einfaches Beispiel ist und dass es viele andere Dinge gibt, die Sie mit der python-docx-Bibliothek tun können, wie z. B. das Lesen und Ändern der Formatierung, Stile und Bilder im Dokument. Weitere Informationen über die Bibliothek und ihre Funktionen finden Sie in ihrer Dokumentation.

### Automatisierung der Bildverarbeitung
In Python kann man Bilder mit verschiedenen Bibliotheken konvertieren, eine davon ist Pillow. Hier ist ein Beispiel, wie man ein Bild in Python mit Pillow von einem Format in ein anderes Format konvertieren kann:
```python
from PIL import Image

# Load the image
img = Image.open("input.jpg")

# Convert the image format
img.save("output.png", "PNG")
```
In diesem Beispiel laden wir das Bild mit der Funktion Image.open und speichern es anschließend mit dem Befehl save in einem anderen Format ab. Hier speichern wir das Bild im PNG-Format.

Man kann auch mehrere Bilder in einem Batch konvertieren, indem man eine Schleife über alle Bilder verwendet. Hier ist ein Beispiel:
```python
import os
from PIL import Image

# Set the input and output directories
input_dir = "input"
output_dir = "output"

# Loop over all images in the input directory
for filename in os.listdir(input_dir):
    # Skip files that are not images
    if not filename.endswith(".jpg"):
        continue
    
    # Load the image
    img = Image.open(os.path.join(input_dir, filename))
    
    # Convert the image format
    new_filename = os.path.splitext(filename)[0] + ".png"
    img.save(os.path.join(output_dir, new_filename), "PNG")
```
Größenänderung von Bildern
```python
from PIL import Image

# Open the image
image = Image.open("original.jpg")

# Resize the image
new_image = image.resize((800, 600))

# Save the resized image
new_image.save("resized.jpg")
```