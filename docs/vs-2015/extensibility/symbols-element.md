---
title: Symbole Element | Microsoft-Dokumentation
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
- Symbols element (VSCT XML schema)
- VSCT XML schema elements, Symbols
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d36bcf22d012d4543267d1b57d41567baf3e85b1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47514927"
---
# <a name="symbols-element"></a>Symbols-Element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Symbols-Element](https://docs.microsoft.com/visualstudio/extensibility/symbols-element).  
  
Definiert GUIDs und IDs, die durch andere VSCT-Elemente verwendet werden. Für nicht verwalteten Code, diese Informationen in der Regel stammen aus den Headerdateien, die vom angegebenen [Extern-Element](../extensibility/extern-element.md). Verwalteten Code verwendet die untergeordneten Elemente des Symbols-Element, um diese Informationen zu definieren.  
  
 Wenn Sie eine VSCT-Datei aus einer vorhandenen CTO-Datei erstellen, werden die Symbole als untergeordnete Elemente des Elements Symbole generiert. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen Sie ein. VSCT-Datei aus einem vorhandenen. CTO-Datei](../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md).  
  
 Das Element Symbole dürfen nicht verwechselt werden, mit der [Element definieren](../extensibility/define-element.md), das Name-Wert-Paare für die Verwendung durch den Präprozessor definiert.  
  
## <a name="syntax"></a>Syntax  
  
```  
<Symbols>  
  <GuidSymbol>... </GuidSymbol>  
  <GuidSymbol>... </GuidSymbol>  
</Symbols>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|Keiner||  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|GuidSymbol|Definiert eine GUID-Symbol. GuidSymbol hat zwei obligatorische Attribute: Name-Wert. Der Name ist der Name des Symbols, und der Wert ist der Wert der GUID als Zeichenfolge.<br /><br /> Zum Beispiel:\<GuidSymbol-Name = "guidVsPackage1Pkg" Value = "{c5f54698-101a-4846-84d3-dc748f9cd848}" / >|  
|IDSymbol|Definiert ein Symbol an. IDSymbol hat zwei obligatorische Attribute: Name-Wert. Der Name ist der Name des Symbols, und der Wert ist der Wert des Symbols als Zeichenfolge.<br /><br /> Zum Beispiel:\<IDSymbol-Name = "MyMenuGroup" Value = "0x1020" / >|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[CommandTable-Element](../extensibility/commandtable-element.md)|Das Stammelement der VSCT-Datei.|  
  
## <a name="example"></a>Beispiel  
  
```  
<Symbols>  
  <GuidSymbol name="guidVsPackage1Pkg" value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />  
  <GuidSymbol name="guidVsPackage1CmdSet" value="{cb9dfd7f-2fcc-4a3e-aae8-f7fe30b1cfac}">  
    <IDSymbol name="MyMenuGroup" value="0x1020" />  
    <IDSymbol name="cmdidMyCommand" value="0x0100" />  
    <IDSymbol name="cmdidMyTool" value="0x0101" />  
  </GuidSymbol>  
</Symbols>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

