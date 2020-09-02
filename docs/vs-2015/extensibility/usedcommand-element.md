---
title: Usedcommand-Element | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 91929038d77bcf14c6997f9b60551ed8c9c3b820
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186365"
---
# <a name="usedcommand-element"></a>UsedCommand-Element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ermöglicht einem VSPackage den Zugriff auf einen Befehl, der in einer anderen vsct-Datei definiert ist. Wenn das VSPackage z. b. den standardmäßigen **Kopier** Befehl verwendet, der durch die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Shell definiert ist, können Sie den Befehl einem Menü oder einer Symbolleiste hinzufügen, ohne ihn erneut zu implementieren.  
  
## <a name="syntax"></a>Syntax  
  
```  
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|attribute|Beschreibung|  
|---------------|-----------------|  
|guid|Erforderlich. Der GUID des GUID-ID-Paars, das den Befehl identifiziert.|  
|id|Erforderlich. Die ID des GUID-ID-Paars, das den Befehl identifiziert.|  
|Bedingung|Optional. Siehe [bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|Keine||  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[UsedCommands-Element](../extensibility/usedcommands-element.md)|Gruppiert usedcommand-Elemente und andere usedcommands-Gruppierungen.|  
  
## <a name="remarks"></a>Bemerkungen  
 Durch das Hinzufügen eines Befehls zum- `<UsedCommands>` Element wird der Umgebung von einem VSPackage mitgeteilt [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , dass das VSPackage den Befehl erfordert. Sie sollten ein- `<UsedCommand>` Element für jeden Befehl hinzufügen, der für das Paket erforderlich ist, das möglicherweise nicht in allen Versionen und Konfigurationen von Visual Studio enthalten ist. Wenn das Paket z. b. einen für Visual C++ spezifischen Befehl aufruft, steht der Befehl Benutzern von Visual Web Developer nur dann zur Verfügung, wenn Sie ein- `<UsedCommand>` Element für den Befehl einschließen.  
  
## <a name="example"></a>Beispiel  
  
```  
<UsedCommands>  
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>  
</UsedCommands>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Usedcommands-Element](../extensibility/usedcommands-element.md)   
 [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
