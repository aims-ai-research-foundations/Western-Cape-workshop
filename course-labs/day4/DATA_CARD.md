# MaternalCare ZA

A synthetic, **isiXhosa-first** dataset of 1,000 examples of expectant or new mothers asking a maternal health assistant for help, set in South African township and rural communities. It was built to teach **supervised fine-tuning** of small language models (Gemma 3 1B) in the AI Research Foundations workshops.

> ⚠️ **Educational use only. Not medical advice.** Every conversation is synthetic. The isiXhosa has **not** been reviewed by first-language speakers and the clinical content has **not** been reviewed by clinicians (`review_status: synthetic_unreviewed`). Do not use this dataset, or models trained on it, to advise real patients.

## At a glance

| | |
|---|---|
| Examples | 1,000 (train 800 · validation 100 · test 100) |
| Languages | isiXhosa only 500 (50%) · mostly isiXhosa with English 350 (35%) · mostly English with isiXhosa 100 (10%) · English only 50 (5%) |
| Format | **default:** one message and one reply · **`conversations`:** the full conversations: 1 exchange 600 (60%), 2 exchanges 250 (25%), 3 to 5 exchanges 150 (15%) |
| Risk level | low 525 (52%) · moderate 246 (25%) · high 229 (23%) |
| Topics | Pregnancy information and development (125), Antenatal care and clinic visits (100), Nutrition and lifestyle (75), Common pregnancy symptoms (125), Pregnancy complications and danger signs (125), Labour and childbirth (100), Newborn care (75), Breastfeeding (75), Postpartum maternal health (100), Mental and emotional wellbeing (100) |

## Example

```json
{
 "messages": [
  {
   "role": "user",
   "content": "hi sisi i-clinic yandi-refer for i-scan e-hospital next week ngoLwesithathu. but since izolo ndine-bleeding encinci and isisu sibuhlungu ezantsi. ndilinde i-scan or? abantwana bam ndizobashiya nabani"
  },
  {
   "role": "assistant",
   "content": "Musa ukulinda i-scan. Yiya esibhedlele ngoku. Ukopha, nokuba kuncinci, kunye neentlungu esiswini xa ukhulelwe ziimpawu zengozi ezifuna ukuhlolwa ngoko nangoko. I-scan yeveki ezayo ayinakuthatha indawo yokuhlolwa namhlanje.\n\n- Cela ummelwane okanye usapho bagcine abantwana.\n- Phatha incwadi yakho yekliniki ne-referral letter.\n- Ukuba akukho transport, tsalela u-10177, okanye u-112 ngeselfowuni.\n\nUkuba igazi liyanda okanye iintlungu ziyaqina, tsalela i-ambulensi kwangoko."
  }
 ]
}
```

## Structure

Two configurations, with the same IDs and splits:

- **default** (`data/`): each example is the opening exchange of a conversation: one `user` message and one `assistant` reply.
- **`conversations`** (`conversations/`): the full conversations, with 1 to 5 alternating exchanges.

Each line is one example:

- `id`: unique identifier (for example `MCZA_000123`)
- `messages`: `user` and `assistant` turns, starting with the user and ending with the assistant
- `metadata`: labels for auditing, not for training: `language`, `domain`, `subtopic`, `task`, `pregnancy_stage`, `interaction_type`, `n_user_turns`, `multi_turn_plan`, `risk_level`, `user_context`, `situation`, `age_band`, `township_theme`, `township_detail`, `region`, `emotional_state`, `communication_style`, `health_literacy`, `source_ids`, `reference_notes`, `review_status` (plus `full_conversation_turns` in the default configuration)

```python
from datasets import load_dataset

dataset = load_dataset("Similoluwa/maternalcare-za")                     # single-turn (default)
conversations = load_dataset("Similoluwa/maternalcare-za", "conversations")  # full conversations
```

## How it was generated

Claude (Anthropic) was used to generate synthetic conversations between mothers and a maternal health assistant, grounded in reference notes drawn from South African and WHO maternal health guidelines (see Sources). A coverage plan was used to ensure coverage of different language patterns, health topics, risk levels, pregnancy and postpartum stages, and everyday community situations such as clinic queues, taxi fares and family advice.

The generated 1,000 conversations were split 800/100/100 for train/validation/test subsets, stratified by language pattern, topic and risk level. The test set is reserved for final evaluation. The default configuration keeps each conversation's opening exchange, which is a complete question and answer on its own; for every high-risk conversation, that first reply already gives the urgent-care advice.

## Intended use

- Teaching and learning how to fine-tune and evaluate small language models for a low-resource language and a specialised domain.
- Prototyping research ideas before collecting and validating real data.

**Out of scope:** clinical decision-making, real patient advice, or any deployment without expert review and human oversight.

## Limitations

- **Unvalidated isiXhosa.** The language may contain unnatural phrasing, errors or uneven regional usage. It needs review by first-language speakers.
- **Unvalidated clinical content.** Responses follow the reference notes but have not been checked by midwives or doctors.
- **Synthetic distribution.** Real mothers' messages are messier and more varied. Some scenarios may feel templated.
- **Automated checks are shallow.** They catch format and some safety problems, not every inaccuracy.
- **Time-sensitive details.** Phone numbers and service details were verified in November 2026 and may change.

## Sources

| Source | Organisation | Year |
|---|---|---|
| [National Integrated Maternal and Perinatal Care Guidelines for South Africa, 5th edition](https://knowledgehub.health.gov.za/system/files/elibdownloads/2024-10/Integrated%20Maternal%20and%20Perinatal%20Care%20Guideline_23_10_2024_0.pdf) | National Department of Health | 2024 |
| [WHO recommendations on antenatal care for a positive pregnancy experience](https://www.who.int/publications/i/item/9789241549912) | World Health Organization | 2016 |
| [WHO recommendations: intrapartum care for a positive childbirth experience](https://www.who.int/publications/i/item/9789241550215) | World Health Organization | 2018 |
| [WHO recommendations on maternal and newborn care for a positive postnatal experience](https://www.who.int/publications/i/item/9789240045989) | World Health Organization | 2022 |
| [Infant and young child feeding](https://www.who.int/news-room/fact-sheets/detail/infant-and-young-child-feeding) | World Health Organization | fact sheet |
| [Sudden infant death syndrome (SIDS)](https://www.nhs.uk/conditions/sudden-infant-death-syndrome-sids/) | NHS | reviewed 2025 |
| [Helplines](https://www.sadag.org/) | South African Depression and Anxiety Group | accessed 2026 |
| [Know who you can call in an emergency](https://www.westerncape.gov.za/know-who-you-can-call-emergency) | Western Cape Government | accessed 2026 |

## Licence

[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Created for the AI Research Foundations for Higher Education workshops.
