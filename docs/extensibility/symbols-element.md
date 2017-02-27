---
title: "Symbole-Element | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Symbole-Element (VSCT-XML-Schema)"
  - "VSCT XML-Schemaelemente, Symbole"
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# Symbole-Element
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Definiert GUIDs und IDs, die von anderen VSCT\-Elementen verwendet werden. Für nicht verwalteten Code, diese Informationen in der Regel stammen aus den Headerdateien, die vom angegebenen [Extern\-Element](../extensibility/extern-element.md). Verwaltete Code verwendet die untergeordneten Elemente des Elements Symbole, diese Informationen zu definieren.  
  
 Wenn Sie eine VSCT\-Datei aus einer vorhandenen .cto\-Datei erstellen, werden die Symbole als untergeordnetes Element des Elements Symbole generiert. Weitere Informationen finden Sie unter [Gewusst wie: Erstellen einer VSCT\-Datei anhand einer vorhandenen CTO\-Datei](../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md).  
  
 Das Element Symbole dürfen nicht verwechselt werden, mit der [Definieren von Element](../extensibility/define-element.md), die Name\-Wert\-Paare für die Verwendung durch den Präprozessor definiert.  
  
## Syntax  
  
```  
<Symbols>  
  <GuidSymbol>... </GuidSymbol>  
  <GuidSymbol>... </GuidSymbol>  
</Symbols>  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|Keine||  
  
### Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|GuidSymbol|Definiert einen GUID\-Symbol. GuidSymbol hat zwei obligatorische Attribute: Name und Wert. Der Name ist der Name des Symbols, und der Wert ist der Wert der GUID als Zeichenfolge.<br /><br /> Zum Beispiel: \< GuidSymbol Name \= "guidVsPackage1Pkg" Value \= "{c5f54698\-101a\-4846\-84d3\-dc748f9cd848}" \/ \>|  
|IDSymbol|Definiert ein Symbol. IDSymbol hat zwei obligatorische Attribute: Name und Wert. Der Name ist der Name des Symbols, und der Wert ist der Wert des Symbols als Zeichenfolge.<br /><br /> Zum Beispiel: \< IDSymbol Name \= "MyMenuGroup" Value \= "0x1020" \/ \>|  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[CommandTable\-Element](../extensibility/commandtable-element.md)|Das Stammelement der .vsct\-Datei.|  
  
## Beispiel  
  
```  
<Symbols> <GuidSymbol name="guidVsPackage1Pkg" value="{c5f54698-101a-4846-84d3-dc748f9cd848}" /> <GuidSymbol name="guidVsPackage1CmdSet" value="{cb9dfd7f-2fcc-4a3e-aae8-f7fe30b1cfac}"> <IDSymbol name="MyMenuGroup" value="0x1020" /> <IDSymbol name="cmdidMyCommand" value="0x0100" /> <IDSymbol name="cmdidMyTool" value="0x0101" /> </GuidSymbol> </Symbols>  
```  
  
## Siehe auch  
 [Visual Studio\-Befehl\-Tabelle \(. VSCT\) Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)