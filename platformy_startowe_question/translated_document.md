# Translated Document

## 3_Opis_problemów_i_potrzeb_rynkowych_Problem_Statement

**Who has a problem?**

*   **Seniors 60+** want to handle their affairs online independently (banking, ZUS, post office, communicators), but are blocked by complex interfaces and the lack of immediate on-screen guidance. In Poland, about 7.2 million people aged 55-74 lack basic digital skills. Globally, the 60+ population is about 1.08 billion.
*   **Families aged 20-50** are the real decision-makers and informal technical guardians. They spend an estimated 3-5 hours per month supporting a senior. Nationally, this amounts to about 86 million hours annually, equivalent to 40,000 FTEs and an opportunity cost of PLN 1.9-3.0 billion.
*   **Local institutions** (Universities of the Third Age, cultural centers, NGOs, banks) conduct classes but lack a tool that scales the number of people in a course and provides a safe space for seniors to learn and test their skills.

**Scale and Urgency**

In the EU, among the 65-74 age group, the deficit of basic digital skills is about 66-75%, depending on the country. The lack of support at the point of the problem translates into real losses. People aged 60+ in the US lost $3.4 billion to scams in 2023. In Poland, estimates indicate about PLN 0.5 billion in losses in 2024 and a risk of up to 250,000 unauthorized transactions in 2025. 75% of people aged 50-80 have experienced an attempted scam, and about 30% have fallen victim. The combination of an aging population with the digitization of services creates a lasting and growing business potential for tools that bridge the competency gap.

**Needs Validation**

We confirmed our theses in preliminary interviews with 10 people conducting courses for seniors. Most indicated that the problem is not a lack of educational content, but the lack of a safe environment in which a senior can repeatedly and independently complete an action on their own screen.

**What is the real problem?**

A senior does not need another video or a general chatbot. They need immediate, contextual, and safe guidance exactly on their screen at a critical step of the process—the barrier to finalizing an action without sharing passwords and without switching windows.

**Why do existing solutions fail?**

*   **Video tutorials and articles** are passive and require reproducing steps from memory.
*   **Hotlines, family, and remote desktops** do not scale, generate frustration, and pose privacy risks.
*   **LLM-based solutions** operate in a text dialogue without the native context of the interface and do not pin tips to UI elements.
*   **On-site training** does not transfer to daily practice after returning home.

This analysis proves that Dodem, by offering real-time support on the user's screen, has significant competitive advantages over passive and non-scalable alternatives.

**Consequences of no solution**

*   **Senior:** fear, resignation from services, procedural errors, several times higher exposure to fraud.
*   **Family:** 3-5 hours of support per month, which amounts to 40+ hours per year, or a week of work, and an opportunity cost of PLN 540-1,680 per household.
*   **Institutions:** after training, 50-70% of participants need re-intervention in the first week, which reduces the effectiveness of the programs. Trainers mentioned situations where people with low digital skills forgot how to operate a given program after just a few hours.

**The explicit need**

Guide me now, on my screen, step by step and safely. The support must be active, contextual, universal for the bank, ZUS, post office, and communicators, private, and available on demand.

**Why now?**

The combination of interface recognition technology, LLM models, and a curated knowledge base allows for the first time to provide economically scalable on-screen support in real time, which eliminates the barrier to finalizing actions.

**Success indicators from the problem perspective**

More tasks completed without help, fewer errors in logging in and payments, shorter time to complete typical activities, fewer interventions from family and institutions.

---

## 2_Opis_zgłaszanego_pomysłu_biznesowego

Dodem is a comprehensive assistive technology solution for seniors (60+) and their families. The application introduces interactive support in every desktop application and browser, displaying real-time "bubbles" with precise step-by-step instructions. The idea grew out of real needs, namely the many hours of telephone explanations of simple operations (banking, mail, communicators) for our parents and grandparents, and the observation that video tutorials, hotlines, and chatbots do not provide immediate, contextual, and private help exactly where the senior is stuck.

There are about 1,078 million people aged 60+ in the world. In the EU, only 25–34 percent of people aged 65–74 have basic digital skills, which means a deficit of 66–75 percent. This gap translates into millions of login, payment, and correspondence handling attempts that end in resignation from the service or a request for help from the family.

Dodem is an on-screen assistive technology assistant for seniors and their loved ones. In real time, it displays contextual step-by-step hints directly on the user's screen, in every desktop application and browser. The key innovation is a contextual guidance engine with deterministic anchoring to interface elements, which recognizes the window state and pins hints to the correct buttons and fields in applications on Windows and macOS and in the browser. Dodem Memory curates official instructions into short, clear steps. Privacy is ensured by local masking of sensitive data, no password logging, encryption, and minimal retention. The result is greater independence for seniors and real time savings for families.

**Solution Architecture (3 pillars):**

*   **Client Application (Windows, macOS; later iOS/Android)** – a lightweight client that tracks the UI structure and user events, with auto-positioning of bubbles over the correct interface elements.
*   **AI Engine** – integration with LLM APIs (OpenAI, Anthropic, Google Gemini) generates short, verified instructions; in the pipeline, proprietary ML models for recognizing UI elements and matching context.
*   **"Dodem Memory"** – a proprietary knowledge base fed with official manuals, PDF files, and transcriptions of video tutorials; elimination of so-called AI "hallucinations" through source curation and validation rules.

**Business Model and Distribution:**

*   **B2C:** subscriptions – including Standard at PLN 39/month and a Family Pack (one configuration supports several devices in the family).
*   **B2B2C:** SaaS licenses for Universities of the Third Age, foundations, and banks (implementation fee + e-learning modules, onboarding workshops).
*   **Channels:** Dodem.pl store, Microsoft Store, Apple App Store, a network of local partners (UTWs, cultural centers, medical facilities, NGOs).

**Why now and why us:** aging societies and the rapid digitization of public/financial services are creating a competency gap that existing tools do not close. Dodem provides active, contextual mentoring "at the point of click," which directly translates into independence for seniors and relief for families. Dodem for seniors focuses on the digital independence of the 60+ and their loved ones through intuitive bubbles and a knowledge base.

---

## 1_Skrócony_opis_pomysłu

Dodem is an assistant that displays simple hints directly on the computer screen, guiding seniors step-by-step through online banking or government portals. Because it works in any application without needing to be modified and uses its own verified knowledge base, it provides precise and safe guidance, giving older people a sense of digital independence. The goal is for the senior to feel as if a coach/mentor is standing behind them, showing them where to click in a safe environment.

---

## 9_Opis_profilu_klienta_docelowego

**Buyer Persona: Marek, 45 years old**

Anna's son, a working manager, the informal "family IT guy." He receives 2-4 calls a week asking for help, sometimes connecting remotely.

**Marek's Motivations:**

*   His mom's safety
*   Saving time and nerves
*   Reducing remote interventions.

**User Persona: Anna, 72 years old**

A retiree, independent in her normal life.

She would like to handle her banking matters online or view photos from her grandchildren's vacation on a large screen, independently of her son.

**Anna's Needs:** When I try to handle a matter online and get stuck, I want to get an immediate hint on my screen so that my actions don't break anything. I would like to complete the task on my own without asking my family for help.

**Marek's Needs:** When I'm working and my mom needs urgent technical help, I want to have a tool that will guide her on her screen, so I can have peace of mind and be sure that she is acting safely and independently.

**Functional User Segmentation**

1.  **Beginners and Anxious Users** – require micro-steps and high-contrast messages on the screen. They need many repetitions to consolidate their knowledge.
2.  **Moderately Independent Users** – are blocked by a single, critical step.
3.  **Users with Visual, Hearing, or Motor Impairments** – need larger bubbles and fonts, as well as simple, WCAG-compliant messages.

**Partner Institutions as a Channel of Reach:**

Universities of the Third Age, cultural centers, libraries, banks, pharmacies, clinics, NGOs, and social service centers. Their need: a tool that transfers learning from the classroom directly to the senior's screen, without integration on the systems side. Cooperation criteria: quick pilot of 2–4 weeks, data protection compliance, ready-made scenarios, and effect reports.

**Customer Journey – From Awareness to Loyalty**

**Awareness:**
Marek will see an ad on Instagram/LinkedIn or an article after another call from his mom;
Anna will hear about the solution at a UTW meeting.

**Consideration:**
Marek checks reviews and compares prices;
Anna asks a friend from her group.

**Decision and Implementation:**
Marek buys a subscription online and configures his mom's profile in 10 minutes; the first use is paying a bill together.

**Success and Value:**
Anna independently completes subsequent tasks—banking, mail, e-health—and sees clear bubbles exactly where she clicks. Marek gets fewer calls, regains time and peace of mind.

**Retention and Development:**
Repeatable monthly tasks, new scenarios in Dodem Memory, the possibility of extending to other devices in the family, and enabling offline mode for the most common tasks.

**Most Common Objections and Answers**

*   **Privacy:** privacy by design, local data masking, no password logs, encryption, full telemetry control.
*   **Will it work with my bank and applications?:** multi-environment without provider-side integration, support for Windows, macOS, and browsers.
*   **Won't it be too difficult?:** 10-minute onboarding, step-by-step bubbles, printed materials, and TTS.

**Success from the Customer's Perspective**

Anna completes more tasks without help, makes fewer errors in critical steps, and performs typical activities faster. Marek reduces the number of interventions and stress, gaining hours per month. The institution sees an increase in the independence of participants and hard outcome indicators in pilot reports.

**Purchase Criteria:**

Effectiveness in real tasks, privacy without access to passwords, quick start in 10 minutes, step-by-step materials. Price acceptance: Standard approx. PLN 39/month.

---

## 8_Charakterystyka_segmentu_klientów_do_których_kierowany_będzie_produkt

The target market for the product includes two complementary segments: seniors aged 60+, who struggle with digital exclusion and fear of technology, and their families (aged 20-50), who are looking for an effective and secure way to remotely support their loved ones. The key motivation for seniors is to regain digital independence, while for their children and grandchildren, the main value is saving time and ensuring the protection of sensitive data of older family members.

Of course, I'll explain step by step:

This sentence describes who the customer of the Dodem product is, dividing them into two main but related groups:

1.  **First group (end user): Seniors 60+**
    *   **Problem:** These individuals often feel lost in the digital world. They are afraid of clicking something wrong, losing money, or being scammed. This uncertainty and lack of skills mean they cannot handle matters online independently, which is termed "digital exclusion."
    *   **Need/Motivation:** They want to regain independence and a sense of control. They wish to independently, without asking for help, make a bank transfer, pick up an e-prescription, or write an email to their grandchildren.

2.  **Second group (buyer and decision-maker): Families of seniors (children, grandchildren aged 20-50)**
    *   **Problem:** Family members spend a lot of time repeatedly explaining the same simple actions over the phone. They often have to use a remote desktop, which can be frustrating and violates the senior's privacy. They are also concerned about the security of their loved ones' data.
    *   **Need/Motivation:** They want to save their time and nerves, while also providing the senior with an effective and secure tool to support them. They care about peace of mind, knowing that their parent or grandparent is protected and can manage.

**In summary:** The product is designed to simultaneously solve the senior's problem (by giving them independence) and their family's problem (by saving them time and providing a sense of security). These two groups are "complementary" because the need of one drives the purchasing decision of the other—the family buys the product to help the senior, who becomes its main user.

**Buyer and Decision-Maker.** Most often a family member aged 20–50, children or grandchildren, often responsible for the senior's formal affairs. Their pains are repetitive calls for help, remote desktop sessions, and relationship tensions. Motivations are time savings, peace of mind, and the assurance of the parent's or grandparent's data security. Key decision criteria are simplicity of implementation, effectiveness in real tasks, privacy without interference with passwords, and a reasonable price in a family subscription model. Typical purchase triggers are the first login to the bank, bill payment, e-prescription, the need to download an official document, and a new phone or computer for the senior. Price acceptance: Standard around PLN 39 per month, Family Pack for several devices in the family.

**Main End User.** Seniors 60+ with low or uneven digital skills, wanting to independently carry out daily online activities in banking, public administration, mail, communicators, and e-health. We distinguish three sub-segments: beginners and anxious individuals, who need very simple, short on-screen tips and high contrast; moderately independent individuals, who are blocked by a critical step on the screen; people with visual, hearing, or motor impairments, requiring larger hitboxes, TTS, simple messages, and WCAG compliance. The main barriers are fear of error and losing money, complex interfaces, lack of immediate on-screen guidance, and working memory overload when switching windows. Motivations are independence, security, contact with family, and the ability to handle matters without visiting offices and banks. UX requirements include large fonts and clickable elements, high contrast, unambiguous steps, one decision per screen, and no jargon.

**Partner Institutions in the B2B2C Channel.** Universities of the Third Age, cultural centers, libraries, banks, pharmacies, clinics, NGOs, and social service centers. Their pains are the low effectiveness of traditional training after leaving the classroom, the lack of a tool that transfers learning directly to the user's screen, limited instructor resources, and GDPR risks. Motivations are real digital inclusion with measurable progress indicators, the image of a helping institution, and loyalty of seniors and families. Cooperation criteria are no integration on the systems side, ready-made scenarios and workshops, data protection compliance, a quick pilot of 2–4 weeks, and effect reports.

**Market Size in TAM, SAM, SOM Standard.**
TAM is the global 60+ population, about 1,078 million people worldwide (UN, World Population Prospects 2022). In the EU, in the 65–74 age group, 25–34 percent of the population has basic digital skills, which implies a deficit of 66–75 percent and confirms the scale of the competency gap (Eurostat 2023, Digital skills). We define SAM as developed and English-speaking markets with a significant digital skills deficit, conservatively about 60.6 million users based on demographic data and the availability of B2B2C channels. We realistically assume SOM at 0.1 percent of SAM in a 36-month horizon, i.e., about 60,600 paying users, with a focus on Poland and selected EU markets and in English-speaking countries. This structure reflects operational capabilities and the planned sales ramp-up.

**Acquisition and Use Paths.** In B2C, we will use educational campaigns aimed at families, a product website, the Microsoft Store and App Store marketplace, and a family referral program. Onboarding takes up to 10 minutes and ends with the first task successes in the bank, mail, and communicators. In B2B2C, we focus on pilots in UTWs and cultural centers, support stands in bank branches and clinics, vouchers from pharmacies and libraries, and introductory workshops, with reporting on the number of tasks completed without help and error reduction.

**Retention and Cyclicality of Use.** Banking and administrative activities are repeated monthly. We assume an average of about 9 months of active use per year. Retention is driven by the effectiveness of on-screen tips, data privacy, and offline mode for the most common tasks.

**Risks and Their Neutralization.** We address the lack of trust in new tools through privacy by design and clear messages about what the application sees and what it does not save. We neutralize the complexity of interfaces by deterministically pinning bubbles to UI elements. We bypass the organizational barriers of institutions with pilots without integration and short license agreements.

---

## 5_Opis_nowych_lub_znacząco_udoskonalonych_cech

Dodem is an assistant that displays simple hints directly on the computer screen, guiding seniors step-by-step through online banking or government portals. It's as if a mentor were standing behind the senior, showing them where to click on the monitor screen.

1.  **Universal UI Support System without Provider-Side Integration**
    A universal engine for contextual interface support without provider-side integration means that the client on Windows and macOS detects the interface structure and window state, then precisely pins hints to specific elements in desktop applications or the browser. The solution does not require building manual paths for new applications and maintains stable positioning during scrolling and window resizing. This is a significant improvement at least at the European level in the AgeTech segment, as it combines desktop and web environments with deterministic anchoring of bubbles without the need for integration on the part of banks or government offices. The user thus receives precise and immediate guidance where they are actually working, which reduces the number of errors and shortens the time to complete tasks.

2.  **Dodem Memory with a High-Relevance Task Instruction Engine**
    Dodem Memory with a high-relevance task instruction engine uses a RAG architecture based on curated sources such as official manuals, PDF files, and video transcriptions. The LLM shortens and simplifies content into concise micro-steps, while validation rules and task templates limit generative errors. Knowledge updates are done on the cloud side without the need to publish a new client version. This is a new feature at the European level because the built-in software for curating and validating LLM results increases the credibility of the hints compared to general text assistants. The value for the user is clear, consistent, and short steps that genuinely reduce cognitive load and speed up task completion in critical processes.

3.  **Privacy and Safety by Design**
    Privacy and Safety by Design ensures local masking of sensitive data, no password logging, encryption in transit and at rest, and minimal retention, with each session conducted with informed consent. Built-in security rules enforce additional confirmations in higher-risk steps, such as entering a transfer amount. The solution is a significant improvement at the global level in data protection, as it introduces built-in client-side anonymization software and eliminates the need to take control of the device as in remote desktop tools. The value for the user and institutions is a high level of trust and the ability to provide help without violating privacy.

4.  **Offline Mode and Edge Processing**
    Offline mode and client-side processing are based on a cache of the most common paths and local data analysis, which allows for maintaining a low hint delivery time—ultimately down to 1.5 seconds—even with a weak connection or temporary lack of internet. This is a significant improvement at the global level, as the consumer segment rarely offers contextual on-screen guidance that also works without constant network access. The user gains continuity of operation and reliability in critical moments such as logging in, making payments, and handling correspondence.

5.  **Accessibility and Ease of Use Designed for 60+**
    Accessibility and ease of use designed for the needs of people aged 60+ include compliance with WCAG 2.2 AA, large fonts and clickable areas, high contrast, voice narration, simple language, and a one-decision-per-screen model. This is a significant improvement in ease of use at the national level, and in combination with direct on-screen guidance, it represents a unique proposition in the Polish ecosystem of digital support for seniors. The user goes through onboarding faster, is less likely to give up at an early stage, and achieves greater independence in daily tasks.

---
