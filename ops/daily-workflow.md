# Daily Idea of the Day Publishing Workflow

1. Search Gmail for the latest `from:notifications@mail.ideabrowser.com subject:"Idea of the Day"` message.
2. If message ID has not been processed:
   - extract subject, body, idea title, product name, and full idea URL;
   - fetch full web page when available;
   - generate public plan repo contents;
   - create public GitHub repo;
   - record processed message ID.
3. If no new message, do nothing.
