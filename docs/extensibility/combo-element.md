---
title: Combo-Element | Microsoft-Dokumentation
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
ms.openlocfilehash: 00ecabcf90e63b18961a828c12ae300be359b5a1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49839985"
---
# <a name="combo-element"></a>Combo-element
Definiert die Befehle, die in einem Kombinationsfeld angezeigt werden. Es gibt vier Arten von Kombinationsfelder, die folgenden: Kombinationsfeld, DynamicCombo, IndexCombo und MRUCombo.  
  
## <a name="syntax"></a>Syntax  
  
```xml 
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
|guid|Erforderlich. GUID der Befehls-ID der GUID-ID.|  
|ID|Erforderlich. ID des Befehls-ID der GUID-ID.|  
|defaultWidth|Erforderlich. Eine ganze Zahl, die eine Breite für das Kombinationsfeld in Pixel angibt.|  
|idCommandList|Erforderlich. Eine ID, die an das Ziel der aktiven Befehl gesendet wird, zum Abrufen der Liste der Elemente, die im Kombinationsfeld angezeigt werden. Die ID wird im gleichen Bereich wie das Steuerelement GUID sein.|  
|priority|Dies ist optional. Ein numerischer Wert, der die Priorität angibt.|  
|Typ|Dies ist optional. Ein Enumerationswert, der den Typ der Schaltfläche angibt.<br /><br /> Wenn nicht angegeben wird, wird die Schaltfläche verwendet.<br /><br /> Kombinationsfeld<br /> Das VSPackage ist verantwortlich für das Auffüllen der Inhalt für dieses Kombinationsfelds. Der Benutzer kann nicht alle von diesem Dropdown-Liste im Textfeld eingeben.<br /><br /> DynamicCombo<br /> Das VSPackage ist verantwortlich für das Auffüllen der Inhalt dieses Kombinationsfelds. Der Benutzer kann dieses Kombinationsfeld Bearbeiten und auch Elemente darin auswählen.<br /><br /> IndexCombo<br /> Identisch mit DynamicCombo, außer dass sie löst den Index des Elements statt dessen Text aus.<br /><br /> MRUCombo<br /> Durch die integrierte Entwicklungsumgebung (IDE) für das VSPackage gefüllt.  Der Benutzer kann in diesem Kombinationsfeld bearbeiten. In der IDE sind bis zu 16 zuletzt Einträge pro im Kombinationsfeld.<br /><br /> Wenn der Benutzer etwas im Kombinationsfeld auswählt oder etwas Neues eingibt, benachrichtigt die IDE das entsprechende VSPackage.|  
|Bedingung|Dies ist optional. Finden Sie unter [bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|Übergeordnetes Element|Dies ist optional. Das übergeordnete Element der Schaltfläche.|  
|CommandFlag|Erforderlich. Finden Sie unter [commandflag-Element](../extensibility/command-flag-element.md). Gültige Werte für eine Schaltfläche CommandFlag sind wie folgt aus.<br /><br /> -CaseSensitive<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DynamicVisibility<br /><br /> – Filter-Schlüssel<br /><br /> -IconAndText<br /><br /> -NoAutoComplete<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -StretchHorizontally|  
|Zeichenfolgen|Erforderlich. Finden Sie unter [Strings-Element](../extensibility/strings-element.md). Das untergeordnete ButtonText-Element muss definiert werden.|  
|Anmerkung|Optionaler Kommentar.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Commands-element](../extensibility/commands-element.md)|Stellt die Auflistung von Befehlen auf der Symbolleiste des VSPackage.|  
  
## <a name="example"></a>Beispiel  
  
```xml  
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
 [Visual Studio-Befehlstabellen (VSCT)-Befehlsdateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
