---
title: MSBuild-Bedingungen | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, conditions
- conditions [MSBuild]
ms.assetid: 9d7aa308-b667-48ed-b4c9-a61e49eb0a85
caps.latest.revision: "14"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b42dadc5a606bcbd94334a070cc571607576dcc9
ms.sourcegitcommit: 03a74d29a1e0584ff4808ce6c9e812b51e774905
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2018
---
# <a name="msbuild-conditions"></a>MSBuild-Bedingungen
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] unterstützt bestimmte Bedingungen, die angewendet werden können, wenn ein `Condition`-Attribut zulässig ist. Diese Bedingungen sind in der folgenden Tabelle angegeben.  
  
|Bedingung|description|  
|---------------|-----------------|  
|'`stringA`' == '`stringB`'|Ergibt `true`, wenn `stringA` gleich `stringB`.<br /><br /> Zum Beispiel:<br /><br /> `Condition="'$(CONFIG)'=='DEBUG'"`<br /><br /> Für einfache alphanumerische Zeichenfolgen und boolesche Werte sind keine einfachen Anführungszeichen erforderlich. Allerdings sind einfache Anführungszeichen für leere Werte erforderlich.|  
|'`stringA`' != '`stringB`'|Ergibt `true`, wenn `stringA` ungleich `stringB`.<br /><br /> Zum Beispiel:<br /><br /> `Condition="'$(CONFIG)'!='DEBUG'"`<br /><br /> Für einfache alphanumerische Zeichenfolgen und boolesche Werte sind keine einfachen Anführungszeichen erforderlich. Allerdings sind einfache Anführungszeichen für leere Werte erforderlich.|  
|\<, >, \<=, >=|Wertet die numerischen Werte der Operanden aus. Gibt `true` aus, wenn die relationale Auswertung TRUE ist. Die Auswertung von Operanden muss eine dezimale oder hexadezimale Zahl ergeben. Hexadezimale Zahlen müssen mit „0x“ beginnen. **Hinweis:** Im XML müssen die Zeichen `<` und `>` mit Escapezeichen versehen werden. Das Symbol `<` wird als `&lt;` dargestellt. Das Symbol `>` wird als `&gt;` dargestellt.|  
|Exists('`stringA`')|Ergibt `true`, wenn eine Datei oder ein Ordner mit dem Namen `stringA` vorhanden ist.<br /><br /> Zum Beispiel:<br /><br /> `Condition="!Exists('$(builtdir)')"`<br /><br /> Für einfache alphanumerische Zeichenfolgen und boolesche Werte sind keine einfachen Anführungszeichen erforderlich. Allerdings sind einfache Anführungszeichen für leere Werte erforderlich.|  
|HasTrailingSlash('`stringA`')|Ergibt `true`, wenn die angegebene Zeichenfolge entweder einen nachgestellten umgekehrten Schrägstrich (\\) oder einen Schrägstrich (/) enthält.<br /><br /> Zum Beispiel:<br /><br /> `Condition="!HasTrailingSlash('$(OutputPath)')"`<br /><br /> Für einfache alphanumerische Zeichenfolgen und boolesche Werte sind keine einfachen Anführungszeichen erforderlich. Allerdings sind einfache Anführungszeichen für leere Werte erforderlich.|  
|!|Ergibt `true`, wenn die Auswertung des Operanden `false` ergibt.|  
|Und|Ergibt `true`, wenn die Auswertung beider Operanden `true` ergibt.|  
|Oder|Ergibt `true`, wenn die Auswertung von mindestens einem Operanden `true` ergibt.|  
|()|Gruppierungsmechanismus, dessen Auswertung `true` ergibt, wenn die Auswertung der darin enthaltenen Ausdrücke `true` ergibt.|  
|$if$ ( %expression% ), $else$, $endif$|Überprüft, ob das angegebene `%expression%` dem Zeichenfolgenwert des übergebenen benutzerdefinierten Vorlagenparameters entspricht. Wenn die Auswertung der `$if$`-Bedingung `true` ergibt, werden die jeweiligen Anweisungen ausgeführt. Andernfalls wird die `$else$`-Bedingung überprüft. Wenn die Auswertung der `$else$`-Bedingung `true` ergibt, werden die jeweiligen Anweisungen ausgeführt. Andernfalls beendet die `$endif$`-Bedingung die Auswertung des Ausdrucks.<br /><br /> Anwendungsbeispiele finden Sie unter [Visual Studio Project/Item Template Parameter Logic](http://stackoverflow.com/questions/6709057/visual-studio-project-item-template-parameter-logic) (Projekte in Visual Studio/Elementlogik für Vorlagenparameter).|  
  
## <a name="see-also"></a>Siehe auch  
 [MSBuild Reference](../msbuild/msbuild-reference.md)  (MSBuild-Referenz)  
 [Conditional Constructs](../msbuild/msbuild-conditional-constructs.md)  (Bedingte Konstrukte in MSBuild)  
 [Exemplarische Vorgehensweise: Erstellen einer neuen MSBuild-Projektdatei](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)
