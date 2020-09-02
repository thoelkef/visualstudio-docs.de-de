---
title: Usedcommands-Element | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- UsedCommands
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 5e000ee0-a919-46e9-9277-2a0659f1eb78
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ba37458e0f8abca27047574170ab8aa3cc7a44ce
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186291"
---
# <a name="usedcommands-element"></a>UsedCommands-Element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das usedcommands-Element gruppiert usedcommand-Elemente und andere usedcommands-Gruppierungen.  
  
 Das usedcommands-Element ist optional. Wenn Sie keine Befehle anrufen, die außerhalb des Pakets definiert sind, müssen Sie diesen Abschnitt nicht in die vsct-Datei einschließen.  
  
## <a name="syntax"></a>Syntax  
  
```  
<UsedCommands condition="Defined(DEBUG)">  
  <UsedCommand ... />  
</UsedCommands>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|attribute|Beschreibung|  
|---------------|-----------------|  
|Bedingung|Optional. Siehe [bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[UsedCommand-Element](../extensibility/usedcommand-element.md)|Der Befehl, der von anderem Code implementiert wird.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[CommandTable-Element](../extensibility/commandtable-element.md)|Definiert alle Elemente, die Befehle darstellen (z. b. Menü Elemente, Menüs, Symbolleisten und Kombinations Felder), die ein VSPackage für die integrierte Entwicklungsumgebung (Integrated Development Environment, IDE) bereitstellt.|  
  
## <a name="example"></a>Beispiel  
  
```  
<UsedCommands>  
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>  
</UsedCommands>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Usedcommand-Element](../extensibility/usedcommand-element.md)   
 [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
