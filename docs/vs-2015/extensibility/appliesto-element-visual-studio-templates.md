---
title: AppliesTo-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8fb1334b-d78c-405f-98b4-786e9f6b58d7
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f7e00fa30d3c2f2b1bfa31152584227bb56639eb
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49218269"
---
# <a name="appliesto-element-visual-studio-templates"></a>AppliesTo-Element (Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Legt einen optionalen Ausdruck fest, um eine oder mehrere Funktionen auszuwählen. (siehe <xref:Microsoft.VisualStudio.Shell.Interop.VsProjectCapabilityExpressionMatcher>). Funktionen werden von Projekttypen über die Hierarchie als Eigenschaft <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID5> verfügbar gemacht. Dadurch kann die Vorlage von mehreren Projekttypen gemeinsam genutzt werden, die über geläufige anwendbare Funktionen verfügen.  
  
 Dieses Element ist optional. Es kann maximal eine Instanz in einer Vorlagendatei geben. Dieses Element ermöglicht einer Elementvorlage nur, auf Grundlage der Funktionen des ausgewählten aktiven Projekts als anwendbar zu optieren. Es kann nicht verwendet werden, um eine Elementvorlage nicht anwendbar zu machen. Wenn `AppliesTo` fehlt oder der Ausdruck nicht erfolgreich optiert, wird `TemplateID` oder `TemplateGroupID` verwendet, um die Vorlage anwendbar zu machen, wie mit früheren Versionen des Produkts.  
  
 Eingeführt in Visual Studio 2013 Update 2. Um die richtige Version verweisen zu können, finden Sie unter [verweisen auf Assemblys, die in Visual Studio 2013 SDK Update 2 übermittelten](http://msdn.microsoft.com/en-us/42b65c3e-e42b-4c39-98c8-bea285f25ffb).  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<AppliesTo >  
  
## <a name="syntax"></a>Syntax  
  
```  
<AppliesTo>Capability1</AppliesTo>   
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
 Keine  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
 Keine  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Kategorisiert die Vorlage.|  
  
## <a name="text-value"></a>Textwert  
 Ein Textwert ist erforderlich. Dieser Text gibt die Funktionen des Projekts an.  
  
 Gültige Ausdruckssyntax ist folgendermaßen definiert:  
  
-   Der Funktionsausdruck, wie z. B. "(VisualC &#124; CSharp) + (MSTest &#124; NUnit)".  
  
-   Die "&#124;" ist der OR-Operator.  
  
-   Die Zeichen "&" und "+" sind beide AND-Operatoren.  
  
-   Das Zeichen "!" ist der Operator NOT.  
  
-   Klammern erzwingen die Auswertungsreihenfolge.  
  
-   Eine leerer oder NULL-Ausdruck wird als Übereinstimmung ausgewertet.  
  
-   Projektfunktionen können jedes Zeichen außer diesen reservierten Zeichen sein: "'' :;,+-*/\\! ~&#124;& %$@^() ={}[] <>? \t\b\n\r  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel werden drei unterschiedliche Vorlagen gezeigt. `Template1` gilt für alle C#-Projekttypen oder jeden anderen Projekttyp, der die `WindowsAppContainer`-Funktion unterstützt. `Template2` gilt für C#-Projekte beliebiger Art. `Template3` gilt für C#-Projekte, die keine `WindowsAppContainer` sind Projekte.  
  
```xml  
<!--  Template 1 -->  
<?xml version="1.0" encoding="utf-8"?>  
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <AppliesTo>CSharp | WindowsAppContainer</AppliesTo>   
    </TemplateData>  
</VSTemplate>  
  
<!--  Template 2 -->  
<?xml version="1.0" encoding="utf-8"?>  
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <AppliesTo>CSharp</AppliesTo>   
    </TemplateData>  
</VSTemplate>  
  
<!--  Template 1 -->  
<?xml version="1.0" encoding="utf-8"?>  
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <AppliesTo>CSharp_Class + (!WindowsAppContainer)</AppliesTo>   
    </TemplateData>  
</VSTemplate>  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)

