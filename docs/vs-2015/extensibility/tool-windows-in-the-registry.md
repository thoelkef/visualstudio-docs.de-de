---
title: Tool Fenster in der Registrierung | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186382"
---
# <a name="tool-windows-in-the-registry"></a>Toolfenster in der Registrierung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPackages, die Tool Fenster bereitstellen, müssen sich bei [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] als Tool Fenster Anbieter registrieren. Tool Fenster, die mithilfe der Visual Studio-Paket Vorlage erstellt wurden, führen dies standardmäßig aus. Tool Fenster Anbieter verfügen über System Registrierungsschlüssel, die Sichtbarkeits Attribute angeben, wie z. b. die standardmäßige Größe und den Speicherort des Tool Fensters, die GUID des Fensters, das als Tool Fensterbereich dient, und den Andock Stil.  
  
 Während der Entwicklung werden Tool Fenster von verwalteten Tool Fenstern durch Hinzufügen von Attributen zum Quellcode und anschließendem Ausführen des RegPkg.exe Hilfsprogramms für die resultierende Assembly registriert. Weitere Informationen finden Sie unter [Registrieren eines Tool Fensters](../extensibility/registering-a-tool-window.md).  
  
## <a name="registering-unmanaged-tool-window-providers"></a>Registrieren nicht verwalteter Tool Fenster Anbieter  
 Nicht verwaltete Tool Fenster Anbieter müssen sich bei [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] im ToolWindows-Abschnitt der Systemregistrierung registrieren. Das folgende. reg-Datei Fragment zeigt, wie ein dynamisches Tool Fenster registriert werden kann:  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\<version number>\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}]  
@="{01069cdd-95ce-4620-ac21-ddff6c57f012}"  
"Name"="Microsoft.Samples.VisualStudio.IDE.ToolWindow.DynamicWindowPane"  
"Float"="250, 250, 410, 430"  
"DontForceCreate"=dword:00000001  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}\Visibility]  
"{f1536ef8-92ec-443c-9ed7-fdadf150da82}"=dword:00000000  
```  
  
 Im ersten Schlüssel im obigen Beispiel ist die Versionsnummer die Version von, z. b. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 7,1 oder 8,0, der Unterschlüssel {f0e1e9a1-9860-484d-ad5d-367d79aabf55} ist die GUID des Tool Fenster Bereichs (dynamicwindowpane), und der Standardwert {01069cdd-95ce-4620-Ac21-ddff6c57f012} ist die GUID des VSPackage, das das Tool Fenster bereitstellt. Eine Erläuterung der Unterschlüssel "float" und "DontForceCreate" finden Sie unter [Anzeige Konfiguration für Tool Fenster](../extensibility/tool-window-display-configuration.md).  
  
 Der zweite optionale Schlüssel, toolwindows\visibility, gibt die GUIDs von Befehlen an, die erfordern, dass das Tool Fenster sichtbar gemacht wird. In diesem Fall sind keine Befehle angegeben. Weitere Informationen finden Sie unter [Konfiguration der Tool Fenster Anzeige](../extensibility/tool-window-display-configuration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Grundlegendes zu VSPackages](../misc/vspackage-essentials.md)
