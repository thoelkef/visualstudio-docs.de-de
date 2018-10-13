---
title: UsedCommands-Element | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- UsedCommands
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 5e000ee0-a919-46e9-9277-2a0659f1eb78
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fe7f29fabb62b7f7703ad501d332c9d37c1e47b8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49276367"
---
# <a name="usedcommands-element"></a>UsedCommands-Element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UsedCommands-Element gruppiert UsedCommand-Elementen und anderen UsedCommands Gruppierungen.  
  
 UsedCommands-Element ist optional. Wenn Sie Befehle, die außerhalb des Pakets definiert nicht aufrufen, müssen Sie nicht in diesem Abschnitt in der VSCT-Datei enthalten.  
  
## <a name="syntax"></a>Syntax  
  
```  
<UsedCommands condition="Defined(DEBUG)">  
  <UsedCommand ... />  
</UsedCommands>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|Bedingung|Dies ist optional. Finden Sie unter [bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[UsedCommand-Element](../extensibility/usedcommand-element.md)|Der Befehl, der durch anderen Code implementiert wird.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[CommandTable-Element](../extensibility/commandtable-element.md)|Definiert die Elemente aus, die Befehle (z. B. Menüelemente, Menüs, Symbolleisten und Kombinationsfeldern), die eine VSPackage bietet die integrierte Entwicklungsumgebung (IDE) darstellen.|  
  
## <a name="example"></a>Beispiel  
  
```  
<UsedCommands>  
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>  
</UsedCommands>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [UsedCommand-Element](../extensibility/usedcommand-element.md)   
 [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

