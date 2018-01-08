---
title: UsedCommand Element | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 06375b45e21e0b83c62f2509d666b786479ff2b4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="usedcommand-element"></a>UsedCommand-Element
Ermöglicht eine VSPackage, um einen Befehl zuzugreifen, der in eine andere VSCT-Datei definiert ist. Angenommen, Ihr VSPackage standardmäßiger **Kopie** Befehl, der definiert wird die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Shell, Sie können den Befehl zu einem Menü oder einer Symbolleiste ohne hinzufügen erneut zu implementieren.  
  
## <a name="syntax"></a>Syntax  
  
```  
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|guid|Erforderlich. Die GUID der der GUID-ID-Paar, die den Befehl bezeichnet.|  
|ID|Erforderlich. Die ID der der GUID-ID-Paar, die den Befehl bezeichnet.|  
|Bedingung|Dies ist optional. Finden Sie unter [bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|Keiner||  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[UsedCommands-Element](../extensibility/usedcommands-element.md)|Gruppen UsedCommand Elementen und anderen UsedCommands Gruppierungen.|  
  
## <a name="remarks"></a>Hinweise  
 Durch einen Befehl zum Hinzufügen der `<UsedCommands>` Element, eine VSPackage informiert die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ab, das VSPackage der-Befehl erfordert. Sie sollten Hinzufügen einer `<UsedCommand>` -Element für jeden Befehl, der das Paket erfordert, dass möglicherweise nicht in allen Versionen und Konfigurationen von Visual Studio enthalten sein. Z. B. Wenn Ihr Paket einen Befehl, die Visual C++-spezifisch ist aufruft, der Befehl wird nicht für Benutzer von Visual Web Developer, sofern Sie eine `<UsedCommand>` -Element für den Befehl.  
  
## <a name="example"></a>Beispiel  
  
```  
<UsedCommands>  
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>  
</UsedCommands>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [UsedCommands-Element](../extensibility/usedcommands-element.md)   
 [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)