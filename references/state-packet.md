# 状态包结构与 /merge 模式

生成（/learn）、解析、校验（/write、/check 前置）或合并（/merge）状态包时，必须遵守本文件。

## 一、状态包 JSON 结构

状态包必须使用以下 JSON 结构：

```json
{
  "version": "author-next-fragment-distribution-v2",
  "source_scope": "对本次素材范围的简短说明",
  "corpus_stats": {
    "scene_types": [
      "素材中出现的场景类型"
    ],
    "pov": [
      "素材中出现的视角"
    ],
    "registers": [
      "素材中出现的语域"
    ],
    "notes": [
      "素材长度、覆盖范围或不足"
    ]
  },
  "global_controls": {
    "max_active_fragments_per_scene": 5,
    "avoid_fragment_piling": true,
    "prefer_implicit": true,
    "allow_background_fragments": true,
    "allow_delayed_echo": true
  },
  "prose_profile": {
    "avg_sentence_length": 0,
    "short_sentence_ratio_le8": 0,
    "exclamation_per_1k_chars": 0,
    "dialogue_line_ratio": 0,
    "paren_monologue_per_1k_chars": 0,
    "method": "取样口径说明，例如：从素材抽取3段各1500字实测"
  },
  "context_axes": {
    "scene_types": [
      "争吵",
      "告别",
      "重逢",
      "试探",
      "亲密",
      "冷战",
      "审问",
      "日常",
      "危机",
      "回忆"
    ],
    "relationship_states": [
      "疏远",
      "试探",
      "靠近",
      "防备",
      "僵持",
      "松动",
      "失控",
      "掩饰",
      "保护",
      "撤退"
    ],
    "tension_levels": [
      "low",
      "medium",
      "high",
      "critical"
    ],
    "narrative_stages": [
      "opening",
      "development",
      "turn",
      "climax",
      "aftermath"
    ],
    "pov": [
      "第一人称",
      "第三人称限知",
      "全知",
      "旁观者",
      "回忆视角"
    ],
    "registers": [
      "现代",
      "都市",
      "校园",
      "悬疑",
      "古风",
      "战争",
      "科幻",
      "日常",
      "职场"
    ]
  },
  "fragments": [
    {
      "id": "frag_001",
      "surface": "片段原文",
      "layer": "micro | punctuation | lexical | address | action | imagery | space | body | dialogue_move | narration_move | camera_move | rhythm | scene_transition",
      "functions": [
        "interruption",
        "avoidance",
        "boundary",
        "distance_change",
        "exposure",
        "pressure",
        "delay",
        "echo",
        "shift",
        "silence"
      ],
      "positions": [
        "句首",
        "句中",
        "句尾",
        "对话开头",
        "对话结尾",
        "叙述转折"
      ],
      "contexts": {
        "scene_types": [],
        "relationship_states": [],
        "tension_levels": [],
        "narrative_stages": [],
        "pov": [],
        "registers": []
      },
      "before_states": [
        "该片段出现前的常见语言状态"
      ],
      "next_distribution": [
        {
          "candidate": "后继片段原文或后继类型",
          "candidate_type": "punctuation | word | phrase | action | environment | silence | body | response | object | camera_cut | memory | delay",
          "weight": "high | medium | low",
          "conditions": [],
          "evidence": []
        }
      ],
      "next_not": [
        "该片段后作者通常不接的内容或写法"
      ],
      "co_occurrence": [
        "常与该片段共现的其他片段"
      ],
      "recurrence": {
        "count": 0,
        "pattern": "复现方式",
        "variations": []
      },
      "sentence_effects": [
        "对句长、标点、节奏的影响"
      ],
      "evidence": [
        "原文证据片段1",
        "原文证据片段2"
      ],
      "confidence": "high | medium | low | insufficient"
    }
  ],
  "transitions": [
    {
      "id": "trans_001",
      "from_id": "frag_001",
      "from_surface": "前驱片段原文",
      "to_surface": "后继片段原文或后继类型",
      "to_type": "punctuation | word | phrase | action | environment | silence | body | response | object | camera_cut | memory | delay",
      "layer_relation": "within_micro | cross_layer | rhythm_cut | camera_cut | response | avoidance | long_range_echo",
      "conditions": {
        "scene_types": [],
        "relationship_states": [],
        "tension_levels": [],
        "narrative_stages": [],
        "pov": [],
        "registers": []
      },
      "relation": "immediate_punctuation | phrase_completion | action_cut | environment_cut | silence | response | avoidance | distance_change | rhythm_change | information_delay | boundary | exposure | echo",
      "function": "该转移在原文中的具体作用，必须用可观察语言事实描述",
      "weight": "high | medium | low",
      "evidence": [
        "原文证据片段1",
        "原文证据片段2"
      ],
      "counterexamples": [
        "反例或不适用情况"
      ],
      "confidence": "high | medium | low | insufficient"
    }
  ],
  "functional_patterns": [
    {
      "id": "func_001",
      "name": "功能模式名称",
      "observable_triggers": [
        "可观察的触发语言事实"
      ],
      "typical_successors": [
        "常见后继"
      ],
      "forbidden_successors": [
        "作者通常避免的后继"
      ],
      "evidence": [
        "原文证据"
      ],
      "confidence": "high | medium | low | insufficient"
    }
  ],
  "chains": [
    {
      "id": "chain_001",
      "name": "片段链名称",
      "trigger": "触发该链条的片段或情境",
      "conditions": {
        "scene_types": [],
        "relationship_states": [],
        "tension_levels": [],
        "narrative_stages": []
      },
      "sequence": [
        "第一个片段",
        "第二个片段",
        "第三个片段",
        "第四个片段"
      ],
      "evidence": [
        "原文证据"
      ],
      "usage": "后续写作时如何使用该链条"
    }
  ],
  "scene_curves": [
    {
      "id": "curve_001",
      "scene_type": "场景类型",
      "stage_sequence": [
        "opening",
        "development",
        "turn",
        "climax",
        "aftermath"
      ],
      "language_changes": [
        "每个阶段的语言变化，例如句长变化、对话比例、动作插入、环境声插入"
      ],
      "evidence": [
        "原文证据"
      ],
      "usage": "后续写作时如何使用该场景曲线"
    }
  ],
  "long_range": [
    {
      "id": "lr_001",
      "element": "意象、称呼、动作、短语、空间或身体感受",
      "first_state": "首次出现时的语言状态",
      "later_states": [
        "后续出现时的变化"
      ],
      "transformation": "该元素如何变奏",
      "evidence": [
        "原文证据"
      ],
      "usage": "后续写作时如何使用该长程复现"
    }
  ],
  "character_graphs": [
    {
      "name": "人物名",
      "aliases": [
        "其他称呼"
      ],
      "baseline": {
        "high_frequency_surfaces": [
          "该人物高频使用的字、词、语气词、标点"
        ],
        "punctuation": [
          "常用标点"
        ],
        "sentence_length": "短 | 中 | 长 | 不稳定",
        "address_patterns": {
          "对某人的称呼": "常用称呼及变化"
        }
      },
      "state_machine": [
        {
          "state": "guarded | probing | softening | avoiding | lying | ashamed | attacking | withdrawing | collapsing | protecting | testing | resigned",
          "trigger": "触发该状态的条件",
          "surfaces": [
            "该人物常输出的字、词、语气词、短句"
          ],
          "moves": [
            "该人物常出现的动作、沉默、视线变化、身体反应"
          ],
          "punctuation": [
            "常用标点"
          ],
          "sentence_length": "短 | 中 | 长 | 不稳定",
          "address_shift": "称呼变化",
          "narration_follow": [
            "该人物回应后，叙述通常跟随什么"
          ],
          "not_do": [
            "该人物在该状态下通常不会做什么"
          ],
          "evidence": [
            "原文证据"
          ]
        }
      ],
      "relationship_differences": [
        "对不同人物说话时的语言差异"
      ],
      "rules": [
        "后续写作时必须遵守的人物语言规则"
      ],
      "evidence": [
        "原文证据"
      ]
    }
  ],
  "rhythm_rules": [
    {
      "id": "rhythm_001",
      "condition": "某种语言状态，例如长句后、连续对话后、问句后、沉默后",
      "contexts": {
        "scene_types": [],
        "relationship_states": [],
        "tension_levels": [],
        "narrative_stages": []
      },
      "next": "作者通常接什么，例如短句、动作、环境声、物品、身体感受",
      "not_next": [
        "作者通常不接什么"
      ],
      "evidence": [
        "原文证据"
      ],
      "confidence": "high | medium | low | insufficient"
    }
  ],
  "negative_space": [
    {
      "id": "neg_001",
      "condition": "某种上下文条件",
      "author_avoids": "作者通常避免的写法",
      "observable_alternative": "作者通常使用的替代写法",
      "evidence": [
        "原文证据"
      ],
      "confidence": "high | medium | low | insufficient"
    }
  ],
  "anchors": [
    {
      "type": "narration | dialogue | conflict | character_voice | imagery | rhythm",
      "content": "原文锚点片段",
      "related_fragments": [
        "相关片段 id 或原文"
      ]
    }
  ],
  "notes": [
    "证据不足、冲突、需要后续补充的内容"
  ]
}
```

## 二、状态包填写规则

1. `fragments` 优先提取真正有牵引力的片段；不要为了数量凑数。
2. 如果素材足够，尽量提取不少于 12 个高牵引片段；如果素材不足，可少于 12 个，但必须在 `notes` 中说明。
3. `transitions` 优先提取稳定转移；如果素材足够，尽量提取不少于 20 条；如果素材不足，可少于 20 条，但必须在 `notes` 中说明。
4. `character_graphs` 只提取有足够语言证据的人物。
5. `evidence` 必须来自用户素材，不得编造。
6. `next_distribution` 必须尽量区分不同上下文条件下的后继候选。
7. `next_not` 必须记录作者通常避免的后继。
8. `weight` 不得随意标高。证据少时必须标 `low` 或 `insufficient`。
9. `functions` 必须使用可观察功能，不得使用空泛风格词。
10. `contexts` 无法判断时填空数组，并在 `notes` 中说明。
11. 不要把 `fragments` 写成普通词表。
12. 不要把 `transitions` 写成剧情概括。
13. 不要把 `character_graphs` 写成人物性格卡。
14. 不要在状态包中插入"他是一个很温柔的人"这类句子。
15. 不要输出 JSON 注释。
16. 不要输出非法 JSON。
17. `prose_profile` 必须在 /learn 时从素材实测填写（抽样≥2段、每段≥1500字，分母写进 `method`）；/merge 时按来源分段保留或加权合并，禁止丢弃。它承载语域层指标（句长、感叹密度、对白比例、独白密度）——这些是片段网络覆盖不到的"文体像不像"因素。
18. `recurrence.count` 是素材内实际出现次数，与 `confidence` 互相独立：confidence 回答"出现时是否稳定"，count 回答"出现得多频繁"。写作时的文体权重由两者共同决定，缺一会导致"高牵引但低频"的指纹被过度使用。

## 三、/merge 模式

当用户输入：

```text
/merge
【状态包1开始】
……
【状态包1结束】

【状态包2开始】
……
【状态包2结束】
```

你进入合并模式。

### 3.1 合并目标

将多个状态包合并为一个更稳定、更条件化、更不易过拟合的片段转移网络。

### 3.2 合并规则

1. 去除重复片段。
2. 相同片段的证据、后继分布、转移关系、负空间可以合并。
3. 如果不同状态包对同一片段有冲突结论，保留冲突记录，并降低置信度。
4. 不要把单次偶然现象泛化为稳定规则。
5. 不要新增没有证据的内容。
6. 如果某片段只出现在特定场景、特定人物关系或特定叙事阶段，必须保留条件限制。
7. 如果多个状态包来自不同语域或题材，必须在 `contexts` 中区分，不得无条件混合。
8. 合并后仍必须遵守所有禁令。
9. 合并禁止设置数量上限（如"最多保留N个片段/人物图"）。合并只做无损操作：去重、并证据、并后继分布、标注来源。状态包过大不构成裁剪理由——选择性只允许发生在写作时的检索层（见 write.md 第3节）。原因：跨素材出现率高的往往只有标点级微指纹，而人物语音、句型、单卷特有规律恰恰依赖"低频但关键"的条目；设上限会系统性地把它们删光。

### 3.3 /merge 输出格式

只输出：

```text
合并完成。

【状态包开始】
{
  ……合并后的完整 JSON 状态包……
}
【状态包结束】
```

在 ZCode 环境中支持文件写入：同时用 Write 工具覆盖或更新当前工作目录的 `author_next_fragment_state.json`。
