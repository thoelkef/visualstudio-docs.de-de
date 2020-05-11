---
title: Gilt Für Element (Visual Studio-Vorlagen) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 8fb1334b-d78c-405f-98b4-786e9f6b58d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 39b5ee1e3cad0b4d8ddbe0fc2dfa1c2d478ec063
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740076"
---
# <a name="appliesto-element-visual-studio-templates"></a>AppliesTo-Element (Visual Studio-Vorlagen)

Gibt einen optionalen Ausdruck an, der <xref:Microsoft.VisualStudio.Shell.Interop.VsProjectCapabilityExpressionMatcher>mit einer oder mehreren Funktionen übereinstimmt (siehe ). Funktionen werden von Projekttypen über die Hierarchie als Eigenschaft __VSHPROPID5 verfügbar [gemacht. VSHPROPID_ProjectCapabilities](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID5.VSHPROPID_ProjectCapabilities>). Dadurch kann die Vorlage von mehreren Projekttypen gemeinsam genutzt werden, die über geläufige anwendbare Funktionen verfügen.

Dieses Element ist optional. Es kann maximal eine Instanz in einer Vorlagendatei geben. Dieses Element ermöglicht einer Elementvorlage nur, auf Grundlage der Funktionen des ausgewählten aktiven Projekts als anwendbar zu optieren. Es kann nicht verwendet werden, um eine Elementvorlage nicht anwendbar zu machen. Wenn `AppliesTo` fehlt oder der Ausdruck nicht erfolgreich optiert, wird `TemplateID` oder `TemplateGroupID` verwendet, um die Vorlage anwendbar zu machen, wie mit früheren Versionen des Produkts.

Eingeführt in Visual Studio 2013 Update 2. Informationen zum Verweisen auf die richtige Version finden Sie unter [Verweisen auf Assemblys, die im Visual Studio 2013 SDK Update 2 bereitgestellt](/previous-versions/dn632168(v=vs.120))wurden.

```xml
<VSTemplate>
   <TemplateData>
      <AppliesTo>
```

## <a name="syntax"></a>Syntax

```xml
<AppliesTo>Capability1</AppliesTo>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Kategorisiert die Vorlage.|

## <a name="text-value"></a>Textwert

Ein Textwert ist erforderlich. Dieser Text gibt die Funktionen des Projekts an.

Gültige Ausdruckssyntax ist folgendermaßen definiert:

- Der Fähigkeitsausdruck, z. B. "(VisualC &#124; CSharp) + (MSTest &#124; NUnit)".

- Der "&#124;" ist der OR-Operator.

- Die Zeichen "&" und "+" sind beide AND-Operatoren.

- Das Zeichen "!" ist der Operator NOT.

- Klammern erzwingen die Auswertungsreihenfolge.

- Eine leerer oder NULL-Ausdruck wird als Übereinstimmung ausgewertet.

- Projektfunktionen können ein beliebiges Zeichen mit Ausnahme dieser reservierten\\Zeichen sein: "'':;,+-*/ !'&#124;&%'()={}[]<>? \t\b\n\r

## <a name="example"></a>Beispiel

Im folgenden Beispiel werden drei unterschiedliche Vorlagen gezeigt. `Template1`gilt entweder für alle C-Projekttypen oder für `WindowsAppContainer` einen anderen Projekttyp, der die Funktion unterstützt. `Template2`gilt für alle C-Projekte jeglicher Art. `Template3` gilt für C#-Projekte, die keine `WindowsAppContainer` sind Projekte.

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

## <a name="see-also"></a>Weitere Informationen

- [Visual Studio-Vorlagenschemareferenz](../extensibility/visual-studio-template-schema-reference.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
