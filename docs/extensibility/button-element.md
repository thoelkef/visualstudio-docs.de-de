---
title: "Button-Element | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Schaltflächen-Element (VSCT-XML-Schema)"
  - "VSCT XML-Schemaelemente, Schaltflächen"
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Button-Element
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Definiert ein Element, das der Benutzer interagieren kann. Schaltflächen verschiedene Arten möglich: Schaltfläche MenuButton und SplitDropDown.  
  
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
|guid|Erforderlich. GUID des Bezeichners GUID-ID-Befehl.|  
|ID|Erforderlich. ID des Bezeichners GUID-ID-Befehl.|  
|priority|Dies ist optional. Ein numerischer Wert, der die Priorität angibt.|  
|Typ|Dies ist optional. Ein Enumerationswert, der die Art der Schaltfläche angibt.<br /><br /> Wenn nicht angegeben wird, wird die Schaltfläche verwendet.<br /><br /> Schaltfläche<br /> Ein standard-Befehl, der auf der Symbolleiste (in der Regel als "ein Symbol"-Schaltfläche), Menüs und Kontextmenüs angezeigt wird.<br /><br /> MenuButton<br /> Ein Menüelement, das einen Befehl wird nicht ausgeführt, aber einer anderen Menüressource erzeugt.<br /><br /> SplitDropDown<br /> Steuerelemente, z. B. die Schaltflächen zum Rückgängigmachen und wiederholen auf der Standardsymbolleiste in Microsoft Word.|  
|Bedingung|Dies ist optional. Finden Sie unter [bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Übergeordnetes Element](../extensibility/parent-element.md)|Optional. Das übergeordnete Element der Schaltfläche.|  
|[Icon-Element](../extensibility/icon-element.md)|Dies ist optional. Das Symbol der Schaltfläche zugeordnet ist.|  
|[Command-Flag-Element](../extensibility/command-flag-element.md)|Erforderlich. Gültige Werte für eine Schaltfläche CommandFlag sind wie folgt aus.<br /><br /> -AllowParams<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DontCache<br /><br /> -DynamicItemStart<br /><br /> -DynamicVisibility<br /><br /> -FixMenuController<br /><br /> -IconAndText<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -NoShowOnMenuController<br /><br /> -Pict<br /><br /> -PostExec<br /><br /> -ProfferedCmd<br /><br /> -RouteToDocs<br /><br /> -TextCascadeUseBtn<br /><br /> -TextMenuUseButton<br /><br /> -TextChanges<br /><br /> -TextChangesButton<br /><br /> -TextContextUseButton<br /><br /> -TextMenuCtrlUseMenu<br /><br /> -TextMenuUseButton<br /><br /> -TextOnly|  
|[Zeichenfolgen-Element](../extensibility/strings-element.md)|Erforderlich. Das untergeordnete Element [ButtonText Element](../extensibility/buttontext-element.md) muss definiert werden.|  
|Anmerkung|Optionaler Kommentar.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Schaltflächen-Element](../extensibility/buttons-element.md)|Gruppiert die Elemente der Schaltfläche.|  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel definiert eine Schaltfläche in einer VSCT-Datei.  
  
 [!CODE [MenuText#02](../CodeSnippet/VS_Snippets_VSSDK/menutext#02)]  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Befehlstabelle (. VSCT)-Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)