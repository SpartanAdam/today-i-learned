# Send an email using Python (and Outlook)

Using Python, you can send emails automatically using Outlook. The below code can be customised to send an email from Outlook, with ability to attach files and customise subject and body.

```python
import win32com.client as win32

outlook = win32.Dispatch('outlook.application')
mail = outlook.CreateItem(0)
mail.To = 'To recipient'
mail.Subject = 'Subject of message'
mail.Body = 'Subject body'
mail.HTMLBody = '<h2><b> HTML subject body</b></h2>' # this field is optional

# To attach a file to the email (optional) - comment out if not being used
attachment  = "Path to the attachment"
mail.Attachments.Add(attachment)

mail.Send()
```

## Send to multiple recipients

This can be done by using a list and `join` to seperate the values by a `;`, see following the below example:

```python
recipients = ['person_1@email.com', 'person_2@email.com']

outlook = win32.Dispatch('outlook.application')
mail = outlook.CreateItem(0)
mail.To = ";".join(recipients)
mail.Subject = 'Subject of message'
mail.Body = 'Subject body'

mail.Send()
```
