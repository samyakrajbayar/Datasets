---
annotations_creators:
- no-annotation
language:
- en
license: cc-by-4.0
multilinguality:
- monolingual
size_categories:
- 10K<n<1M
source_datasets:
- original
task_categories:
- tabular-classification
task_ids: []
pretty_name: "World Language Structures WALS"
tags:
- tabular
- education
---

# World Language Structures WALS


## ⭐ Upvote & Support
If you find this dataset useful for your research, machine learning projects, or data visualization, please consider giving it an **Upvote**! Your support helps make open data more accessible to the community.


# World Language Structures — WALS Typological Atlas

**Subtitle:** 3,573 languages × 192 structural features: word order, phonology, morphology and grammar.

---

## 📖 Description

### 3,573 languages × 192 structural features

WALS Online (the World Atlas of Language Structures) codes the grammar, phonology and lexicon of
the world's languages. This dataset pivots the whole atlas into one row per language: **3,573
languages** and **214 columns**, of which **192** are individual WALS features
(e.g. `wals_81a_order_of_object_and_verb`) whose values are the human-readable feature values
("Subject-Object-Verb", "Small", ...).

- **Identity** — WALS id, name, Glottolog code, ISO 639-3, family, subfamily, genus, country.
- **Geography** — latitude, longitude and macroarea.
- **Coverage** — features answered, coverage percentage, whether the language is in the 100- or
  200-language sample, family and genus size, isolate flag.
- **Features** — 192 structural variables covering phonology (consonant inventories, tone,
  stress), morphology (case, gender, derivation), word order, numerals, negation and more.

The matrix is **11.1% filled** (76,475 of
686,016 cells); the best-documented language, **English**, has
**159 of 192** features coded. The largest macroareas are
Eurasia (659), Africa (606), Papunesia (560), North America (396), South America (258) and the largest families are
Austronesian (324), Niger-Congo (324), Indo-European (176), Sino-Tibetan (146), Afro-Asiatic (145).

## 🧾 Columns (214)

`wals_id`, `name`, `macroarea`, `latitude`, `longitude`, `glottocode`, `iso639_3`, `family`, `subfamily`, `genus`, `iso_codes`, `country_code`, `source`, `samples_100`, `samples_200`, `features_answered`, `feature_coverage_pct`, `has_iso`, `has_glottocode`, `family_size`, `genus_size`, `is_isolate`, `wals_1a_consonant_inventories`, `wals_2a_vowel_quality_inventories`, `wals_3a_consonant_vowel_ratio`, `wals_4a_voicing_in_plosives_and_fricatives`, `wals_5a_voicing_and_gaps_in_plosive_systems`, `wals_6a_uvular_consonants`, `wals_7a_glottalized_consonants`, `wals_8a_lateral_consonants`, `wals_9a_the_velar_nasal`, `wals_10a_vowel_nasalization`, `wals_10b_nasal_vowels_in_west_africa`, `wals_11a_front_rounded_vowels`, `wals_12a_syllable_structure`, `wals_13a_tone`, `wals_14a_fixed_stress_locations`, `wals_15a_weight_sensitive_stress`, `wals_16a_weight_factors_in_weight_sensitive_str`, `wals_17a_rhythm_types`, `wals_18a_absence_of_common_consonants`, `wals_19a_presence_of_uncommon_consonants`, `wals_20a_fusion_of_selected_inflectional_format`, `wals_21a_exponence_of_selected_inflectional_for`, `wals_21b_exponence_of_tense_aspect_mood_inflect`, `wals_22a_inflectional_synthesis_of_the_verb`, `wals_23a_locus_of_marking_in_the_clause`, `wals_24a_locus_of_marking_in_possessive_noun_ph`, `wals_25a_locus_of_marking_whole_language_typolo`, `wals_25b_zero_marking_of_a_and_p_arguments`, `wals_26a_prefixing_vs_suffixing_in_inflectional`, `wals_27a_reduplication`, `wals_28a_case_syncretism`, `wals_29a_syncretism_in_verbal_person_number_mar`, `wals_30a_number_of_genders`, `wals_31a_sex_based_and_non_sex_based_gender_sys`, `wals_32a_systems_of_gender_assignment`, `wals_33a_coding_of_nominal_plurality`, `wals_34a_occurrence_of_nominal_plurality`, `wals_35a_plurality_in_independent_personal_pron`, `wals_36a_the_associative_plural`, `wals_37a_definite_articles`, `wals_38a_indefinite_articles`, `wals_39a_inclusive_exclusive_distinction_in_ind`, `wals_39b_inclusive_exclusive_forms_in_pama_nyun`, `wals_40a_inclusive_exclusive_distinction_in_ver`, `wals_41a_distance_contrasts_in_demonstratives`, `wals_42a_pronominal_and_adnominal_demonstrative`, `wals_43a_third_person_pronouns_and_demonstrativ`, `wals_44a_gender_distinctions_in_independent_per`, `wals_45a_politeness_distinctions_in_pronouns`, `wals_46a_indefinite_pronouns`, `wals_47a_intensifiers_and_reflexive_pronouns`, `wals_48a_person_marking_on_adpositions`, `wals_49a_number_of_cases`, `wals_50a_asymmetrical_case_marking`, `wals_51a_position_of_case_affixes`, `wals_52a_comitatives_and_instrumentals`, `wals_53a_ordinal_numerals`, `wals_54a_distributive_numerals`, `wals_55a_numeral_classifiers`, `wals_56a_conjunctions_and_universal_quantifiers`, `wals_57a_position_of_pronominal_possessive_affi`, `wals_58a_obligatory_possessive_inflection`, `wals_58b_number_of_possessive_nouns`, `wals_59a_possessive_classification`, `wals_60a_genitives_adjectives_and_relative_clau`, `wals_61a_adjectives_without_nouns`, `wals_62a_action_nominal_constructions`, `wals_63a_noun_phrase_conjunction`, `wals_64a_nominal_and_verbal_conjunction`, `wals_65a_perfective_imperfective_aspect`, `wals_66a_the_past_tense`, `wals_67a_the_future_tense`, `wals_68a_the_perfect`, `wals_69a_position_of_tense_aspect_affixes`, `wals_70a_the_morphological_imperative`, `wals_71a_the_prohibitive`, `wals_72a_imperative_hortative_systems`, `wals_73a_the_optative`, `wals_74a_situational_possibility`, `wals_75a_epistemic_possibility`, `wals_76a_overlap_between_situational_and_episte`, `wals_77a_semantic_distinctions_of_evidentiality`, `wals_78a_coding_of_evidentiality`, `wals_79a_suppletion_according_to_tense_and_aspe`, `wals_79b_suppletion_in_imperatives_and_hortativ`, `wals_80a_verbal_number_and_suppletion`, `wals_81a_order_of_subject_object_and_verb`, `wals_81b_languages_with_two_dominant_orders_of`, `wals_82a_order_of_subject_and_verb`, `wals_83a_order_of_object_and_verb`, `wals_84a_order_of_object_oblique_and_verb`, `wals_85a_order_of_adposition_and_noun_phrase`, `wals_86a_order_of_genitive_and_noun`, `wals_87a_order_of_adjective_and_noun`, `wals_88a_order_of_demonstrative_and_noun`, `wals_89a_order_of_numeral_and_noun`, `wals_90a_order_of_relative_clause_and_noun`, `wals_90b_prenominal_relative_clauses`, `wals_90c_postnominal_relative_clauses`, `wals_90d_internally_headed_relative_clauses`, `wals_90e_correlative_relative_clauses`, `wals_90f_adjoined_relative_clauses`, `wals_90g_double_headed_relative_clauses`, `wals_91a_order_of_degree_word_and_adjective`, `wals_92a_position_of_polar_question_particles`, `wals_93a_position_of_interrogative_phrases_in_c`, `wals_94a_order_of_adverbial_subordinator_and_cl`, `wals_95a_relationship_between_the_order_of_obje`, `wals_96a_relationship_between_the_order_of_obje`, `wals_97a_relationship_between_the_order_of_obje`, `wals_98a_alignment_of_case_marking_of_full_noun`, `wals_99a_alignment_of_case_marking_of_pronouns`, `wals_100a_alignment_of_verbal_person_marking`, `wals_101a_expression_of_pronominal_subjects`, `wals_102a_verbal_person_marking`, `wals_103a_third_person_zero_of_verbal_person_mar`, `wals_104a_order_of_person_markers_on_the_verb`, `wals_105a_ditransitive_constructions_the_verb_gi`, `wals_106a_reciprocal_constructions`, `wals_107a_passive_constructions`, `wals_108a_antipassive_constructions`, `wals_108b_productivity_of_the_antipassive_constr`, `wals_109a_applicative_constructions`, `wals_109b_other_roles_of_applied_objects`, `wals_110a_periphrastic_causative_constructions`, `wals_111a_nonperiphrastic_causative_construction`, `wals_112a_negative_morphemes`, `wals_113a_symmetric_and_asymmetric_standard_nega`, `wals_114a_subtypes_of_asymmetric_standard_negati`, `wals_115a_negative_indefinite_pronouns_and_predi`, `wals_116a_polar_questions`, `wals_117a_predicative_possession`, `wals_118a_predicative_adjectives`, `wals_119a_nominal_and_locational_predication`, `wals_120a_zero_copula_for_predicate_nominals`, `wals_121a_comparative_constructions`, `wals_122a_relativization_on_subjects`, `wals_123a_relativization_on_obliques`, `wals_124a_want_complement_subjects`, `wals_125a_purpose_clauses`, `wals_126a_when_clauses`, `wals_127a_reason_clauses`, `wals_128a_utterance_complement_clauses`, `wals_129a_hand_and_arm`, `wals_130a_finger_and_hand`, `wals_130b_cultural_categories_of_languages_with`, `wals_131a_numeral_bases`, `wals_132a_number_of_non_derived_basic_colour_cat`, `wals_133a_number_of_basic_colour_categories`, `wals_134a_green_and_blue`, `wals_135a_red_and_yellow`, `wals_136a_m_t_pronouns`, `wals_136b_m_in_first_person_singular`, `wals_137a_n_m_pronouns`, `wals_137b_m_in_second_person_singular`, `wals_138a_tea`, `wals_139a_irregular_negatives_in_sign_languages`, `wals_140a_question_particles_in_sign_languages`, `wals_141a_writing_systems`, `wals_142a_para_linguistic_usages_of_clicks`, `wals_143a_order_of_negative_morpheme_and_verb`, `wals_143b_obligatory_double_negation`, `wals_143c_optional_double_negation`, `wals_143d_optional_triple_negation`, `wals_143e_preverbal_negative_morphemes`, `wals_143f_postverbal_negative_morphemes`, `wals_143g_minor_morphological_means_of_signaling`, `wals_144a_position_of_negative_word_with_respect`, `wals_144b_position_of_negative_words_relative_to`, `wals_144c_languages_with_different_word_order_in`, `wals_144d_the_position_of_negative_morphemes_in`, `wals_144e_multiple_negative_constructions_in_svo`, `wals_144f_obligatory_double_negation_in_svo_lang`, `wals_144g_optional_double_negation_in_svo_langua`, `wals_144h_negsvo_order`, `wals_144i_snegvo_order`, `wals_144j_svnego_order`, `wals_144k_svoneg_order`, `wals_144l_the_position_of_negative_morphemes_in`, `wals_144m_multiple_negative_constructions_in_sov`, `wals_144n_obligatory_double_negation_in_sov_lang`, `wals_144o_optional_double_negation_in_sov_langua`, `wals_144p_negsov_order`, `wals_144q_snegov_order`, `wals_144r_sonegv_order`, `wals_144s_sovneg_order`, `wals_144t_the_position_of_negative_morphemes_in`, `wals_144u_double_negation_in_verb_initial_langua`, `wals_144v_verb_initial_with_preverbal_negative`, `wals_144w_verb_initial_with_negative_that_is_imm`, `wals_144x_verb_initial_with_clause_final_negativ`, `wals_144y_the_position_of_negative_morphemes_in`

## 💡 Ideas for using this data

1. **Word order** — map subject-object-verb vs subject-verb-object languages.
2. **Phonology** — consonant inventory size vs latitude or family.
3. **Typology clusters** — cluster languages by their feature vectors.
4. **Family similarity** — which families are typologically most diverse.
5. **Missing data** — documentation coverage by macroarea and family.
6. **Feature correlation** — which grammatical features co-occur.
7. **Isolates** — languages with no relatives and their feature profiles.
8. **Geography** — spatial autocorrelation of structural features.

## 📁 Files

| File | What it is |
|---|---|
| `world_languages.csv` | 3,573 languages x 214 columns, 192 of them WALS features. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`linguistics`, `languages`, `typology`, `wals`, `grammar`, `culture`, `social-science`

## 🔗 Provenance

- **Source:** **WALS Online** CLDF release (`cldf-datasets/wals`, files `languages.csv`,
  `parameters.csv`, `codes.csv`, `values.csv`), based on Dryer & Haspelmath (eds.), *World Atlas
  of Language Structures Online*.
- **Processing:** the long `values` table was pivoted to one column per feature; feature values were
  mapped from numeric codes to their readable labels; coverage, family size, genus size and
  isolate flags were derived.
- **Snapshot date:** 27 November 2026.

## 🔄 Update frequency

**Irregular.** WALS Online is updated when a new edition is released.

## ⚠️ Caveats

- WALS is a sample of about 2,700 languages, not a complete inventory of the world's ~7,000 languages.
- Many languages have only a fraction of the 192 features coded, so the matrix is sparse.
- Feature values are expert judgements and can differ from other typological databases.
- Columns are named after feature IDs and titles; feature definitions live in the WALS chapters.
- Latitude and longitude are representative points, not language boundaries.
- Family and genus follow the WALS classification, which differs from Glottolog in places.

## 📜 Licence

WALS Online, Dryer & Haspelmath (eds.), CC BY 4.0.

