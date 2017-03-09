---
title: "XSD-Aufgabe | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.task.xsd"
  - "VC.Project.VCXMLDataGeneratorTool.Namespace"
  - "VC.Project.VCXMLDataGeneratorTool.GenerateFromSchema"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "XSD-Aufgabe (MSBuild [Visual C++])"
  - "MSBuild (Visual C++), XSD-Aufgabe"
ms.assetid: 15c99f5c-7124-4bbc-bc03-70c7bcce8893
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# XSD-Aufgabe
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Umschließt das XML Schema Definition Tool (xsd.exe), das Schema-oder Klassendateien von einer Quelle generiert.  
  
## <a name="parameters"></a>Parameter  
 Die folgende Tabelle beschreibt die Parameter der **XSD** Aufgabe.  
  
-   **AdditionalOptions**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Eine Liste von Optionen, wie in der Befehlszeile angegeben. Z. B. "*option1/option2 /option#*". Mit diesem Parameter können Optionen angeben, die nicht von einem beliebigen anderen dargestellt werden **XSD** Task-Parameter.  
  
-   **GenerateFromSchema**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Gibt die Typen, die aus dem angegebenen Schema generiert werden.  
  
     Geben Sie einen der folgenden Werte an, von die jeder einer XSD-Option entspricht.  
  
    -   **Klassen** - **/classes**  
  
    -   **DataSet** - **/DataSet**  
  
-   **Sprache**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Gibt die Programmiersprache an, für den generierten Code zu verwenden.  
  
     Wählen Sie aus **CS** (c#, Standardeinstellung), **VB** (Visual Basic), oder **JS** (JScript). Sie können auch einen vollqualifizierten Namen für eine Klasse angeben, die `System.CodeDom.Compiler.CodeDomProvider Class` implementiert.  
  
-   **Namespace**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Gibt den Laufzeitnamespace für die generierten Typen an.  
  
-   **Datenquellen**  
  
     Erforderlicher `ITaskItem[]`-Parameter.  
  
     Definiert ein Array von MSBuild-Quelldateielementen, die verbraucht und von Aufgaben ausgegeben werden können.  
  
-   **SuppressStartupBanner**  
  
     Optionale **booleschen** Parameter.  
  
     Bei `true` wird die Anzeige der Copyright- und Versionsnummernmeldung bei Aufgabenstart verhindert.  
  
-   **TrackerLogDirectory**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Gibt das Verzeichnis für das Nachverfolgungsprotokoll an.  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz zu Aufgaben](../msbuild/msbuild-task-reference.md)