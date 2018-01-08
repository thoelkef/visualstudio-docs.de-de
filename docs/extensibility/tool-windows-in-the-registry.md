---
title: Toolfenster in der Registrierung | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: tool windows, registering
ms.assetid: c4bb8add-7148-49e4-a377-01d059fd5524
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8d3277a4e24b12d409654548b5670a4d47fa9539
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="tool-windows-in-the-registry"></a>Toolfenster in der Registrierung
VSPackages, die Toolfenster bereitstellen müssen bei registrieren [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] als tool Anbietern für Fenster. Toolfenster, die mithilfe der Visual Studio-Paketvorlage erstellt dazu standardmäßig. Tool-Fenster-Anbieter haben Systemregistrierungsschlüssel, die Sichtbarkeitsattribute, z. B. Standardgröße Tool-Fenster und die Position der GUID des Fensters, das als Toolfensterbereich und andockstil dient angeben.  
  
 Während der Entwicklung registrieren verwalteten Tool Fenster Anbieter Toolfenster durch Hinzufügen von Attributen zum Quellcode, und klicken Sie dann das RegPkg.exe-Dienstprogramm für die resultierende Assembly ausführen. Weitere Informationen finden Sie unter [registrieren ein Toolfenster](../extensibility/registering-a-tool-window.md).  
  
## <a name="registering-unmanaged-tool-window-providers"></a>Registrieren von Anbietern für nicht verwalteten Tool-Fenster  
 Nicht verwaltete Tool Fenster Anbieter müssen bei registrieren [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] im Abschnitt ToolWindows der systemregistrierung. Das folgende Fragment einer REG-Datei zeigt, wie eine dynamische Toolfenster registriert werden kann:  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\<version number>\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}]  
@="{01069cdd-95ce-4620-ac21-ddff6c57f012}"  
"Name"="Microsoft.Samples.VisualStudio.IDE.ToolWindow.DynamicWindowPane"  
"Float"="250, 250, 410, 430"  
"DontForceCreate"=dword:00000001  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}\Visibility]  
"{f1536ef8-92ec-443c-9ed7-fdadf150da82}"=dword:00000000  
```  
  
 In den ersten Schlüssel im obigen Beispiel, ist die Versionsnummer die Version des [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], z. B. 7.1 oder 8.0, den Unterschlüssel {f0e1e9a1-9860-484d-ad5d-367d79aabf55} ist die GUID der Toolfensterbereich (DynamicWindowPane) und der standardmäßige Wert {} 01069cdd-95ce-4620-Ac21-ddff6c57f012} ist die GUID des VSPackage das Toolfenster bereitstellen. Eine Erläuterung der Unterschlüssel "float" und DontForceCreate, finden Sie unter [Tool Fenster Anzeigekonfiguration](../extensibility/tool-window-display-configuration.md).  
  
 Der zweite optionale Schlüssel ToolWindows\Visibility, gibt die GUIDs der Befehle, die erfordern das Toolfenster sichtbar gemacht werden sollen. In diesem Fall keine angegebenen Befehle vorhanden sind. Weitere Informationen finden Sie unter [Tool Fenster Anzeigekonfiguration](../extensibility/tool-window-display-configuration.md).  
  
## <a name="see-also"></a>Siehe auch  
 [VSPackages](../extensibility/internals/vspackages.md)