---
title: Kombinationsfeld-Element | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Combos element (VSCT XML schema)
- VSCT XML schema elements, Combos
ms.assetid: 392e3063-f0a0-4130-9583-23bd2aa3fa36
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ca91102467755610144e4d24405e89ace5a013b7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31100938"
---
# <a name="combo-element"></a>Kombinationsfeld-Element
Definiert die Befehle, die in einem Kombinationsfeld angezeigt werden. Gibt es vier Arten von Kombinationsfelder, wie folgt: Kombinationsfeld, DynamicCombo IndexCombo und MRUCombo.  
  
## <a name="syntax"></a>Syntax  
  
```  
<combo guid="guidMyCommandSet" id="MyCommand" defaultWidth="20" idCommandList="MyCommandListID" priority="0x102" type="DropDownCombo">  
  <Parent>... </Parent  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</combo>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|guid|Erforderlich. GUID des Bezeichners GUID-ID-Befehl.|  
|ID|Erforderlich. ID des Bezeichners GUID-ID-Befehl.|  
|defaultWidth|Erforderlich. Eine ganze Zahl, die eine Breite für das Kombinationsfeld in Pixel angibt.|  
|idCommandList|Erforderlich. Eine ID, die an das Ziel der aktiven Befehl gesendet wird, beim Abrufen der Liste der Elemente im Kombinationsfeld angezeigt werden. Die ID wird im gleichen Bereich wie für das Steuerelement GUID sein.|  
|priority|Dies ist optional. Ein numerischer Wert, der die Priorität angibt.|  
|Typ|Dies ist optional. Ein Enumerationswert, der den Typ der Schaltfläche angibt.<br /><br /> Wenn nicht angegeben wird, wird die Schaltfläche verwendet.<br /><br /> Kombinationsfeld<br /> Das VSPackage ist verantwortlich für den Inhalt für dieses Kombinationsfeld ausfüllen. Alle Elemente kann nicht in das Textfeld dieser Dropdownliste eingegeben werden.<br /><br /> DynamicCombo<br /> Das VSPackage ist verantwortlich für den Inhalt dieses Kombinationsfelds ausfüllen. Der Benutzer kann diese Kombinationsfeld Bearbeiten und auch Elemente darin auswählen.<br /><br /> IndexCombo<br /> Identisch mit DynamicCombo, außer dass sie löst den Index des Elements statt dessen Text.<br /><br /> MRUCombo<br /> Von der integrierten Entwicklungsumgebung (IDE) für das VSPackage aufgefüllt.  Der Benutzer kann in diesem Kombinationsfeld bearbeiten. In der IDE sind bis zu 16 zuletzt Einträge pro Kombinationsfeld.<br /><br /> Wenn der Benutzer ein Element im Kombinationsfeld wählt oder etwas Neues eingibt, benachrichtigt die IDE das entsprechende VSPackage.|  
|Bedingung|Dies ist optional. Finden Sie unter [bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|Übergeordnetes Element|Dies ist optional. Das übergeordnete Element der Schaltfläche.|  
|CommandFlag|Erforderlich. Finden Sie unter [Befehl Flag Element](../extensibility/command-flag-element.md). Gültige Werte für eine Schaltfläche CommandFlag sind wie folgt aus.<br /><br /> -CaseSensitive<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DynamicVisibility<br /><br /> -Drücken<br /><br /> -IconAndText<br /><br /> -NoAutoComplete<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -StretchHorizontally|  
|Zeichenfolgen|Erforderlich. Finden Sie unter [Zeichenfolgen Element](../extensibility/strings-element.md). Das untergeordnete ButtonText-Element muss definiert werden.|  
|Anmerkung|Optionaler Kommentar.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Commands-Element](../extensibility/commands-element.md)|Stellt die Auflistung von Befehlen auf der Symbolleiste des VSPackage.|  
  
## <a name="example"></a>Beispiel  
  
```  
<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"  
  defaultWidth="100" idCommandList="cmdidGetInsertOptionsList">  
  <CommandFlag>DynamicVisibility</CommandFlag>  
  <Strings>  
    <ButtonText>Select Insert Options</ButtonText>  
  </Strings>  
</Combo>  
  
<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"  
  priority="0x0500" type="DropDownCombo" defaultWidth="100"  
  idCommandList="cmdidGetInsertOptionsList">  
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">  
  <CommandFlag>DynamicVisibility</CommandFlag>  
  <Strings>  
    <ButtonText>Select Insert Options</ButtonText>  
  </Strings>  
</Combo>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)