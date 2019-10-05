---
title: Tools von Windows in der Registrierung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering
ms.assetid: c4bb8add-7148-49e4-a377-01d059fd5524
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8cedb95ccd98c3d5bd5e05086cfd1b53b0f97cd9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68186382"
---
# <a name="tool-windows-in-the-registry"></a>Toolfenster in der Registrierung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPackages, die Toolfenster bereitstellen, müssen bei registrieren [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] als tool Fenster-Anbieter. Toolfenster erstellt mithilfe der Visual Studio-Paket-Vorlage in der Standardeinstellung werden hierzu. Tool-Fenster-Anbieter müssen die System-Registrierungsschlüssel, die angeben, Visibility-Attribute, z. B. die Standardgröße des Tools und den Speicherort, die GUID des Fensters, das als Tool-Fensterbereich, und andockstil dient.  
  
 Während der Entwicklung registrieren Anbieter von verwalteten Tools Fenster Toolfenster durch Hinzufügen von Attributen zum Quellcode, und klicken Sie dann das Dienstprogramm "RegPkg.exe" auf die sich ergebende Assembly ausgeführt. Weitere Informationen finden Sie unter [Registrieren eines Toolfensters](../extensibility/registering-a-tool-window.md).  
  
## <a name="registering-unmanaged-tool-window-providers"></a>Registrieren von Anbietern für nicht verwaltete Tool-Fenster  
 Nicht verwaltete Tool-Fenster-Anbieter müssen bei registrieren [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] im ToolWindows Abschnitt der Registrierung des Systems. Das folgende Fragment einer REG-Datei zeigt, wie ein dynamischen Toolfensters registriert werden kann:  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\<version number>\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}]  
@="{01069cdd-95ce-4620-ac21-ddff6c57f012}"  
"Name"="Microsoft.Samples.VisualStudio.IDE.ToolWindow.DynamicWindowPane"  
"Float"="250, 250, 410, 430"  
"DontForceCreate"=dword:00000001  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}\Visibility]  
"{f1536ef8-92ec-443c-9ed7-fdadf150da82}"=dword:00000000  
```  
  
 In den ersten Schlüssel im obigen Beispiel, ist die Versionsnummer die Version des [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], z. B. 7.1 oder 8.0 des Unterschlüssels "{f0e1e9a1-9860-484d-ad5d-367d79aabf55}" ist die GUID der Tool-Fensterbereich (DynamicWindowPane) und den standardmäßigen Wert { 01069cdd-95ce-4620-Ac21-ddff6c57f012} ist die GUID des dem VSPackage, das im Toolfenster. Eine Erläuterung der Unterschlüssel "float" und DontForceCreate, finden Sie unter [Tool-Fenster-Anzeigekonfiguration](../extensibility/tool-window-display-configuration.md).  
  
 Der zweite optionale Schlüssel ToolWindows\Visibility, gibt die GUIDs der Befehle, die erfordern das Toolfenster sichtbar gemacht werden sollen. Es gibt in diesem Fall keine Befehle, die angegeben werden. Weitere Informationen finden Sie unter [Tool-Fenster-Anzeigekonfiguration](../extensibility/tool-window-display-configuration.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Grundlegendes zu VSPackage](../misc/vspackage-essentials.md)
