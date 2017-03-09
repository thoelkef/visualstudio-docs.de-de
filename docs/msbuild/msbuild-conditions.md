---
title: "MSBuild Conditions | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, conditions"
  - "conditions [MSBuild]"
ms.assetid: 9d7aa308-b667-48ed-b4c9-a61e49eb0a85
caps.latest.revision: 14
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MSBuild Conditions
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] unterstützt einen bestimmten Satz an Bedingungen, der überall dort angewendet werden kann, wo ein `Condition`\-Attribut zulässig ist.  In der folgenden Tabelle werden diese Bedingungen erläutert.  
  
|Bedingung|Description|  
|---------------|-----------------|  
|'`stringA`' \=\= '`stringB`'|Ergibt `true`, wenn `stringA` gleich `stringB` ist.<br /><br /> Beispiel:<br /><br /> `Condition="'$(CONFIG)'=='DEBUG'"`<br /><br /> Einfache Anführungszeichen sind für einfache alphanumerische Zeichenfolgen oder boolesche Werte nicht erforderlich.  Für leere Werte sind jedoch einfache Anführungszeichen erforderlich.|  
|'`stringA`' \!\= '`stringB`'|Ergibt `true`, wenn `stringA` ungleich  `stringB` ist.<br /><br /> Beispiel:<br /><br /> `Condition="'$(CONFIG)'!='DEBUG'"`<br /><br /> Einfache Anführungszeichen sind für einfache alphanumerische Zeichenfolgen oder boolesche Werte nicht erforderlich.  Für leere Werte sind jedoch einfache Anführungszeichen erforderlich.|  
|\<, \>, \<\=, \>\=|Wertet die numerischen Werte der Operanden aus.  Gibt `true` zurück, wenn die relationale Auswertung den Wert true hat.  Operanden müssen eine dezimale oder hexadezimale Zahl ergeben.  Hexadezimalzahlen müssen mit "0x" anfangen. **Note:**  In XML müssen die Zeichen `<` und `>` mit Escapezeichen versehen werden.  Das Symbol `<` wird als `<` dargestellt.  Das Symbol `>` wird als `>` dargestellt.|  
|Exists\('`stringA`'\)|Ergibt `true`, wenn eine Datei oder ein Ordner mit dem Namen `stringA` vorhanden ist.<br /><br /> Beispiel:<br /><br /> `Condition="!Exists('$(builtdir)')"`<br /><br /> Einfache Anführungszeichen sind für einfache alphanumerische Zeichenfolgen oder boolesche Werte nicht erforderlich.  Für leere Werte sind jedoch einfache Anführungszeichen erforderlich.|  
|HasTrailingSlash\('`stringA`'\)|Ergibt `true`, wenn die angegebene Zeichenfolge entweder einen nachgestellten umgekehrten Schrägstrich \(\\\) oder Schrägstrich \(\/\) enthält.<br /><br /> Beispiel:<br /><br /> `Condition="!HasTrailingSlash('$(OutputPath)')"`<br /><br /> Einfache Anführungszeichen sind für einfache alphanumerische Zeichenfolgen oder boolesche Werte nicht erforderlich.  Für leere Werte sind jedoch einfache Anführungszeichen erforderlich.|  
|\!|Ergibt `true`, wenn der Operand `false` ergibt.|  
|And|Ergibt `true`, wenn beide Operanden `true` ergeben.|  
|Oder|Ergibt `true`, wenn mindestens einer der Operanden `true` ergibt.|  
|\(\)|Gruppierungsmechanismus, der `true` ergibt, wenn darin enthaltene Ausdrücke `true` ergeben.|  
  
## Siehe auch  
 [MSBuild Reference](../msbuild/msbuild-reference.md)   
 [Conditional Constructs](../msbuild/msbuild-conditional-constructs.md)   
 [Walkthrough: Creating an MSBuild Project File from Scratch](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)