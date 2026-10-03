# Privacy Policy for Apology Companion

**Last updated:** 2026-10-03

**Developer:** Boyi Intelligence

Apology Companion ("the app"), published by Boyi Intelligence ("we", "us"), is a voice-first AI companion for processing difficult
interpersonal feelings. This policy describes what data the app handles, where it goes,
and how long it is kept.

## The short version

**We do not receive your data.** The app sends nothing to the developer of this app. There
is no analytics service, no crash reporting, no usage tracking, and no server of ours that
your conversations pass through. We have no ability to read your conversations, hear your
voice, see your photos, or identify you.

**The only destination your data ever has is the AI provider you choose yourself**, in
Settings → AI service. When you send a message, its text goes directly from your device to
that provider — OpenAI, DeepSeek, or NVIDIA — using an API key **you** supply. It does not
pass through us on the way, and we hold no copy.

Everything else — your voice, your recordings, your photos, your conversation history,
your voice clips, your credentials — stays on your device.

**Two optional features are exceptions, and both are off by default.**

- If you switch on "Apology by video", the photo you attached to a role is sent to a
  video-generation service to create a short clip. See "Apology by video" below.
- If you switch voice cloning to **Service** mode, the text of the companion's spoken
  replies is sent to the voice service you choose (ElevenLabs or PlayHT) to be turned
  into speech. Your own words are not sent there. See "Cloud voice services" below.

Nothing is sent to either service while the feature is off.

## What stays on your device

- **Voice recordings.** Speech-to-text runs entirely on-device. There is no cloud speech path in the app at all —
  when a language has no on-device model, the app refuses to transcribe rather than
  uploading your audio.
- **Voice clips you add for voice cloning** (see below), encrypted at rest.
- **Your roles** — the people you set up to talk to — including their names, your notes,
  and any photo you attach. Photos are encrypted at rest, and stay on the device unless
  you switch on "Apology by video" (below).
- **Your conversation history**, encrypted at rest with a per-install key held in the
  device keychain/keystore.
- **Your account credentials.** Accounts are local to the device; the password is stored
  only as a salted PBKDF2 hash.
- **API keys you enter** for an AI provider, stored in the device keychain/keystore.

## What leaves your device

**Conversation text is sent to the AI provider you selected.** By default that is the
only destination. If you turn on the optional cloud voice feature, the companion's replies
are additionally sent to the voice service you chose; see "Cloud voice services" below.

To generate a reply, the app sends the current message plus a short redacted context
directly to the provider you picked in **Settings → AI service**, authenticated with
**your own API key**. You choose the provider; if you have not configured one, the app
sends nothing and tells you to add a key.

This traffic goes straight from your device to that provider over HTTPS. It does not pass
through any server we run, and we receive no copy.
Turning the app's networking off entirely by not configuring a provider is a supported
state — the rest of the app continues to work offline.

Before sending, the app redacts both your message and the context around it: email
addresses and phone numbers are stripped, and specific calendar dates ("15 March 2024")
are replaced with a placeholder. Redaction is a safeguard, not a guarantee — names and
street addresses are not removed, so anything else you write is sent as written.

Once your text reaches the provider, **their** privacy policy and retention rules apply,
under the account your API key belongs to. Please read the policy of whichever provider
you choose.

**Voice model downloads.** The app can download on-device speech models, which are
public files, from `huggingface.co` and `github.com`. No conversation content, account
information or personal data is sent in these requests, but, as with any download, those
hosts can see your device's IP address and standard request metadata. Their privacy
policies apply.

No audio recordings, no voice clips and no history files are ever transmitted. The only
other things that can leave the device are a role's photo (only when you switch on
"Apology by video") and the companion's reply text (only when you switch voice cloning to
Service mode).

## Voice cloning

If you turn on voice cloning, you can add an audio clip of a person, and the app will
generate speech in that voice for that role's replies.

- The clip is **processed and stored only on your device**, encrypted at rest. It is never
  uploaded.
- Synthesis runs entirely on-device.
- The app asks you to confirm that **you have the voice owner's permission** before the
  feature can be enabled. Please only use a voice you are entitled to use. Using
  someone's voice without their permission may be unlawful where you live, and in some
  jurisdictions synthesized speech must be labelled as artificial.
- The cloned voice is used only for the role's own spoken replies. It is never used for
  the app's other voices, and the app does not use it anywhere outside your conversation.
- Deleting the role, replacing the clip, or deleting your account removes the clip from
  the device.

## Cloud voice services

**Off by default.** Voice cloning normally runs entirely on your device (see above). In
Settings you can instead switch it to **Service** mode, where speech is generated by a
third-party voice service using **your own account and API key** with that service. The
app supports **ElevenLabs** and **PlayHT**.

- **What is sent:** the text of each reply the companion speaks, as it is spoken, plus the
  voice you selected on that service and a speaking-rate setting. **What is not sent:**
  your own words, your recordings, your voice clips, your photos, your history and your
  role's background.
- The app asks for a **separate confirmation** before Service mode can be enabled, in
  addition to the voice-cloning confirmation, because it means conversation content leaves
  your device. Switching back to on-device mode stops any further text being sent.
- The request goes directly from your device to the service over HTTPS. It does not pass
  through any server we run, and we receive no copy.
- Once your text reaches the service, **their** privacy policy and retention rules apply,
  under the account your API key belongs to. Please read it before enabling this.
- Your API key for the service is stored in the device keychain/keystore and is removed
  when you delete your account.

## Apology by video

**Off by default.** When you switch it on in Settings, you supply your own credentials for
**Kling** (a video-generation service operated by Kuaishou, a Chinese company), and the app
generates one short clip per role.

- The trigger is **adding a role with a photo**. At that moment the app sends **that
  photo** to Kling, along with a text instruction describing an apologetic expression.
  Kling returns a roughly 10-second video of the person in the photo appearing to offer an
  apology.
- **This is the only feature that transmits a photo.** No conversation text, no audio, no
  voice clips and no other role data are sent to Kling.
- One clip is generated per role, when the role is created — not per message.
- The request goes directly from your device to Kling using your own credentials. It does
  not pass through any server we run, and we receive no copy.
- Once your photo reaches Kling, **their** privacy policy and retention rules apply. Please
  read it before enabling this.
- The app stores only the **link** to the finished video, not the video itself. Those links
  expire, so a clip may stop playing after a while.
- The generated person is synthetic. Only use a photo you have the right to use — animating
  someone's likeness without their permission may be unlawful where you live, and some
  jurisdictions require synthetic video to be labelled as such.
- Switching the feature off stops any further photo being sent. Deleting the role removes
  the photo and the stored link from your device; anything already sent to Kling must be
  removed through Kling.

## Permissions the app asks for

- **Microphone** — to hear you during a conversation. Audio is transcribed on-device and
  is never uploaded.
- **Internet** — to reach the AI provider you chose, the optional services described
  above, and to download voice models (see below).

## Deleting your data

- **Delete a role** to remove that role, its photo, its voice clip and its conversation
  history.
- **Settings → Delete account** permanently erases your account and everything it owns:
  every role you created, all conversations, any voice clips, the stored links to any
  generated videos, every saved API key (AI providers, video generation and cloud voice
  services), the voice-cloning and cloud-voice confirmations you gave, and your
  credentials. This is immediate, happens entirely on the device, and cannot be undone.
- **Uninstalling the app** removes all app data.

Because your data is never sent to a server we control, there is nothing for us to delete
on your behalf. Data held by your chosen AI provider — or by Kling, ElevenLabs or PlayHT,
if you enabled the optional features that use them — must be deleted through that
provider.

## Not currently active

These are present in the codebase but **disabled or unimplemented**, and handle no data
today. This section must be updated before any of them ship:

- **Analytics / telemetry.** No events are recorded or transmitted.
- **Push notifications.** No token is registered.
- **In-app purchases.** No purchase or receipt data is processed.
- **"Share this session" reporting.** Not implemented; nothing is uploaded. (Video
  generation and cloud voice services *are* implemented and are described in their own
  sections above.)

## Children's privacy

The app is not directed at children and is intended for users aged 17 or older. We do not
knowingly collect data from children, and in any case we do not receive your data at all
(see "The short version").

## Changes to this policy

This document is updated when the app's data practices change, with a revised
"Last updated" date.

## Contact

Questions about this policy, or requests relating to your data, can be sent to Boyi Intelligence at:
**byzh_service@sina.com**
