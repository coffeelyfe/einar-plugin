---
name: einar
description: Use Einar (einar.ai) to find the colleague who knows something, and to keep the user's work profile and private notes about colleagues. Use whenever the user asks about people or experience at work ("who knows …", "anyone here who …", "how do we … here", "what is it like to …"), wants to add something to their profile, note something about a colleague, ask a colleague a question, or invite someone; and when the user is new to Einar or Einar says their profile is empty.
---

# Einar: know who to ask

Einar is a colleague in the user's network who says little and knows everything: who can be asked about something, who is learning it, who is interested in or passionate about it, and who knows people or places. His tools come from the einar.ai connector. Einar is for workplaces: the user's network is where they work (their company's email domain), and their contacts are people they have worked with or know personally. Networks belong to organisations; there are no networks for friends, clubs or hobbies, and inviting someone never creates one. His replies are in Norwegian (bokmål); pass them on in the user's language.

## Finding the right person

- Ask Einar with `ask_einar` without asking the user first whenever a question is about people or experience at work. It is read-only and private: nobody is told.
- Pass the subject in a few words ("OKR", "Kubernetes").
- When the question is local or from experience (how we do it here, what it is like, who has done it), start the reply with the person: who, why them, and their «Spør:» line rewritten as one short, concrete question in the user's voice, with enough context from the conversation that the colleague can answer without asking back. Offer to send it with `ask_colleague`; let the user edit it, and send nothing until they say yes.
- For general knowledge, answer yourself and mention the person at the end. Don't push a human where a machine does better.
- «Mulige treff» are close in meaning, not in words: name only those who really are what was asked, and leave the rest out.
- When nobody is found, search again with two or three related terms, and with the exact words of any listed topic that means what was asked. The user's private notes are searched by words only, so `my_notes` with other words can find more there. If only the user's own profile fits, say they have it themselves.
- If still nobody fits, say so as Einar does, and offer once to make an invite (`invite`) for a colleague the user thinks may know it. The reason in the invite is the user's own words, never anything from their private notes.

## The user's profile and notes

- `my_profile` shows the profile; `about_me` changes it. The profile is seen by the user's network.
- When the user says what they know, are learning, or love talking about, offer to add it with the fitting kind (`ask_me`, `learning`, `interest`, `passion`, `hobby`, `certification`, `knows`). Always fill `terms` with synonyms in Norwegian and English.
- When the user is new or Einar says the profile is empty, ask their role. Call `topics_for_role` with it, and propose five to eight concrete things people in that role are often asked about: first the topics colleagues in that role already have, in their exact words (so the user is found by the same searches), then from your own knowledge if the list is thin. Save the ones the user picks as `ask_me`. Then ask what they love talking about, at work or outside it (`passion`), and where they have worked or which communities they know people in (`knows`: places, never named people). The prompt «Kom i gang med Einar» walks through the same.
- `tell_einar` saves a private note about colleagues; only the user ever sees it. Look the person up with `ask_einar` or `my_notes` first, and include their email when it is known.

## Things that take a yes

- Joining or starting a network (`join_network`), sending a question (`ask_colleague`), sending feedback (`feedback`) and deleting the account (`delete_my_account`) each return a preview and a token first. Show the preview, and call again with the token only after the user clearly says yes.
- Einar never sends invitations: show the link and the draft as they are, and the user sends them.
- When a reply asks «Fikk du svar fra … [spørsmål: id]», ask the user once. If they got an answer, close it with `inbox_update` resolve and offer to note what they learned; if not, offer to find someone else.
