---
title: Schaltfläche Element | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ad49fd053a10938dcc9f038ff7385bcd93c6253f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47510412"
---
# <a name="button-element"></a>Button-Element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Schaltflächenelement](https://docs.microsoft.com/visualstudio/extensibility/button-element).  
  
Definiert ein Element, das der Benutzer interagieren kann. Schaltflächen können unterschiedlicher Art sein: Schaltfläche MenuButton und SplitDropDown.  
  
## <a name="syntax"></a>Syntax  
  
```  
<Button guid="guidMyCommandSet" id="MyCommand" priority="0x102" type="button">  
  <Parent>... </Parent>  
  <Icon>... </Icon>  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</Button>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|guid|Erforderlich. GUID der Befehls-ID der GUID-ID.|  
|ID|Erforderlich. ID des Befehls-ID der GUID-ID.|  
|priority|Dies ist optional. Ein numerischer Wert, der die Priorität angibt.|  
|Typ|Dies ist optional. Ein Enumerationswert, der die Art der Schaltfläche angibt.<br /><br /> Wenn nicht angegeben wird, wird die Schaltfläche verwendet.<br /><br /> Schaltfläche<br /> Ein standard-Befehl, der in Symbolleisten (normalerweise als ein Symbol aus), Menüs und Kontextmenüs angezeigt wird.<br /><br /> MenuButton<br /> Ein Menüelement, das einen Befehl nicht ausgeführt, aber ein weiteres Menü erzeugt.<br /><br /> SplitDropDown<br /> Steuerelemente, z. B. die Schaltflächen zum Rückgängigmachen und wiederholen auf der Standardsymbolleiste in Microsoft Word.|  
|Bedingung|Dies ist optional. Finden Sie unter [bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Parent-Element](../extensibility/parent-element.md)|Dies ist optional. Das übergeordnete Element der Schaltfläche.|  
|[Icon-Element](../extensibility/icon-element.md)|Dies ist optional. Das Symbol der Schaltfläche zugeordnet ist.|  
|[CommandFlag-Element](../extensibility/command-flag-element.md)|Erforderlich. Gültige Werte für eine Schaltfläche CommandFlag sind wie folgt aus.<br /><br /> -AllowParams<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DontCache<br /><br /> -DynamicItemStart<br /><br /> -DynamicVisibility<br /><br /> -FixMenuController<br /><br /> -IconAndText<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -NoShowOnMenuController<br /><br /> -Pict<br /><br /> -PostExec<br /><br /> -ProfferedCmd<br /><br /> -RouteToDocs<br /><br /> -TextCascadeUseBtn<br /><br /> -TextMenuUseButton<br /><br /> -TextChanges<br /><br /> -TextChangesButton<br /><br /> -TextContextUseButton<br /><br /> -TextMenuCtrlUseMenu<br /><br /> -TextMenuUseButton<br /><br /> -TextOnly|  
|[Strings-Element](../extensibility/strings-element.md)|Erforderlich. Das untergeordnete Element [ButtonText-Element](../extensibility/buttontext-element.md) muss definiert werden.|  
|Anmerkung|Optionaler Kommentar.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Buttons-Element](../extensibility/buttons-element.md)|Gruppiert Elemente der Schaltfläche.|  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel definiert eine Schaltfläche in einer VSCT-Datei.  
   
 ```xml
<Button guid="guidMenuTextCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
    <Parent guid="guidMenuTextCmdSet" id="MyMenuGroup" />
    <Icon guid="guidImages" id="bmpPic1" />
    <CommandFlag>TextChanges</CommandFlag>
    <Strings>
          <CommandName>cmdidMyCommand</CommandName>
          <ButtonText>My Command name</ButtonText>
    </Strings>
</Button>
 ```

## <a name="see-also"></a>Siehe auch  
 [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
