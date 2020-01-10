---
title: Einstellungen für die .NET-Codierungskonventionen für EditorConfig
ms.date: 06/14/2018
ms.topic: reference
helpviewer_keywords:
- coding conventions [EditorConfig]
- EditorConfig coding conventions
- language code style rules [EditorConfig]
- formatting conventions [EditorConfig]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2c93a6e86ba82a75dabb8b2be77d2a82a3b4d599
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75566240"
---
# <a name="net-coding-convention-settings-for-editorconfig"></a>Einstellungen für die .NET-Codierungskonventionen für „EditorConfig“

Sie können in Ihrer Codebasis das Codeformat mit einer [EditorConfig](../ide/create-portable-custom-editor-options.md)-Datei definieren und verwalten. „EditorConfig“ enthält mehrere wesentliche Formatierungseigenschaften, wie z.B. `indent_style` und `indent_size`. In Visual Studio können Einstellungen für die .NET-Codierungskonventionen auch mit einer EditorConfig-Datei konfiguriert werden. Sie können einzelne .NET-Codierungskonventionen aktivieren oder deaktivieren und konfigurieren, inwieweit die einzelnen Regeln über einen Schweregrad erzwungen werden sollen.

> [!TIP]
> - Wenn Sie Codekonventionen in einer EditorConfig-Datei definieren, konfigurieren Sie damit, wie die in Visual Studio integrierten [Codeformat-Analysetools](../code-quality/roslyn-analyzers-overview.md) Ihren Code analysieren sollen. Die EditorConfig-Datei ist die Konfigurationsdatei für diese Analysetools.
> - Codeformateinstellungen für Visual Studio können auch im Dialogfeld mit den [Text-Editor-Optionen](code-styles-and-code-cleanup.md) festgelegt werden. Die Einstellungen in der EditorConfig-Datei haben jedoch Vorrang, und unter **Optionen** festgelegte Einstellungen sind keinem bestimmten Projekt zugeordnet.

## <a name="convention-categories"></a>Kategorien für Konventionen

Es gibt drei unterstützte Kategorien für .NET-Codierungskonventionen:

- [Sprachkonventionen](../ide/editorconfig-language-conventions.md)

   Regeln für die Sprache C# oder die Sprache Visual Basic. Beispielsweise können Sie Regeln hinsichtlich der Verwendung von `var` oder explizite Typen angeben, wenn Sie Variablen definieren oder Ausdruckskörpermember bevorzugen.

- [Formatierungskonventionen](../ide/editorconfig-formatting-conventions.md)

   Regeln für das Layout und die Struktur Ihres Codes, um diesen lesbarer zu machen. Beispielsweise können Sie Regeln hinsichtlich der geschweiften Klammern (Allman) angeben, oder es werden Leerzeichen in Steuerblöcken bevorzugt.

- [Namenskonventionen](../ide/editorconfig-naming-conventions.md)

   Regeln für die Benennung von Codeelementen. Sie können beispielsweise angeben, dass die `async`-Methoden mit „Async“ enden müssen.

## <a name="example-editorconfig-file"></a>EDITORCONFIG-Beispieldatei

Im Folgenden finden Sie eine *EDITORCONFIG*-Beispieldatei mit den Standardoptionen für die ersten Schritte:

```ini
###############################
# Core EditorConfig Options   #
###############################

root = true

# All files
[*]
indent_style = space

# Code files
[*.{cs,csx,vb,vbx}]
indent_size = 4
insert_final_newline = true
charset = utf-8-bom

###############################
# .NET Coding Conventions     #
###############################

[*.{cs,vb}]
# Organize usings
dotnet_sort_system_directives_first = true
dotnet_separate_import_directive_groups = false

# this. preferences
dotnet_style_qualification_for_field = false:silent
dotnet_style_qualification_for_property = false:silent
dotnet_style_qualification_for_method = false:silent
dotnet_style_qualification_for_event = false:silent

# Language keywords vs BCL types preferences
dotnet_style_predefined_type_for_locals_parameters_members = true:silent
dotnet_style_predefined_type_for_member_access = true:silent

# Parentheses preferences
dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_operators = never_if_unnecessary:silent

# Modifier preferences
dotnet_style_require_accessibility_modifiers = for_non_interface_members:silent
dotnet_style_readonly_field = true:suggestion

# Expression-level preferences
dotnet_style_object_initializer = true:suggestion
dotnet_style_collection_initializer = true:suggestion
dotnet_style_explicit_tuple_names = true:suggestion
dotnet_style_null_propagation = true:suggestion
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_prefer_is_null_check_over_reference_equality_method = true:silent
dotnet_style_prefer_inferred_tuple_names = true:suggestion
dotnet_style_prefer_inferred_anonymous_type_member_names = true:suggestion
dotnet_style_prefer_auto_properties = true:silent
dotnet_style_prefer_conditional_expression_over_assignment = true:silent
dotnet_style_prefer_conditional_expression_over_return = true:silent

###############################
# Naming Conventions          #
###############################

# Style Definitions
dotnet_naming_style.pascal_case_style.capitalization             = pascal_case

# Use PascalCase for constant fields
dotnet_naming_rule.constant_fields_should_be_pascal_case.severity = suggestion
dotnet_naming_rule.constant_fields_should_be_pascal_case.symbols  = constant_fields
dotnet_naming_rule.constant_fields_should_be_pascal_case.style    = pascal_case_style
dotnet_naming_symbols.constant_fields.applicable_kinds            = field
dotnet_naming_symbols.constant_fields.applicable_accessibilities  = *
dotnet_naming_symbols.constant_fields.required_modifiers          = const

###############################
# C# Code Style Rules         #
###############################

[*.cs]
# var preferences
csharp_style_var_for_built_in_types = true:silent
csharp_style_var_when_type_is_apparent = true:silent
csharp_style_var_elsewhere = true:silent

# Expression-bodied members
csharp_style_expression_bodied_methods = false:silent
csharp_style_expression_bodied_constructors = false:silent
csharp_style_expression_bodied_operators = false:silent
csharp_style_expression_bodied_properties = true:silent
csharp_style_expression_bodied_indexers = true:silent
csharp_style_expression_bodied_accessors = true:silent

# Pattern-matching preferences
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion

# Null-checking preferences
csharp_style_throw_expression = true:suggestion
csharp_style_conditional_delegate_call = true:suggestion

# Modifier preferences
csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async:suggestion

# Expression-level preferences
csharp_prefer_braces = true:silent
csharp_style_deconstructed_variable_declaration = true:suggestion
csharp_prefer_simple_default_expression = true:suggestion
csharp_style_pattern_local_over_anonymous_function = true:suggestion
csharp_style_inlined_variable_declaration = true:suggestion

###############################
# C# Formatting Rules         #
###############################

# New line preferences
csharp_new_line_before_open_brace = all
csharp_new_line_before_else = true
csharp_new_line_before_catch = true
csharp_new_line_before_finally = true
csharp_new_line_before_members_in_object_initializers = true
csharp_new_line_before_members_in_anonymous_types = true
csharp_new_line_between_query_expression_clauses = true

# Indentation preferences
csharp_indent_case_contents = true
csharp_indent_switch_labels = true
csharp_indent_labels = flush_left

# Space preferences
csharp_space_after_cast = false
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_between_method_call_parameter_list_parentheses = false
csharp_space_between_method_declaration_parameter_list_parentheses = false
csharp_space_between_parentheses = false
csharp_space_before_colon_in_inheritance_clause = true
csharp_space_after_colon_in_inheritance_clause = true
csharp_space_around_binary_operators = before_and_after
csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
csharp_space_between_method_call_name_and_opening_parenthesis = false
csharp_space_between_method_call_empty_parameter_list_parentheses = false
csharp_space_after_comma = true
csharp_space_after_dot = false

# Wrapping preferences
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true

##################################
# Visual Basic Code Style Rules  #
##################################

[*.vb]
# Modifier preferences
visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async:suggestion
```

## <a name="see-also"></a>Siehe auch

- [Schnelle Aktionen](../ide/quick-actions.md)
- [Erstellen portierbarer benutzerdefinierter Editor-Optionen](../ide/create-portable-custom-editor-options.md)
- [.editorconfig-Datei der .NET Compiler Platform](https://github.com/dotnet/roslyn/blob/master/.editorconfig)
