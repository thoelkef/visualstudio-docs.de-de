---
title: "Toolfenster in der Registrierung | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Toolfenster, registrieren"
ms.assetid: c4bb8add-7148-49e4-a377-01d059fd5524
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Toolfenster in der Registrierung
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPackages die Toolfenster angeben, muss mit [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Toolfenster als Anbieter registrieren.  Die Toolfenster, die erstellt werden, indem sie die Vorlage Visual Studio\-Paket hierfür verwenden standardmäßig.  Toolfenster Systemregistrierungs Anbieter haben, die von Sichtbarkeits Attribute, z. B. Toolfenster Standard Größe und Position, die GUID des Fensters, das als Tool und dient fensterbereich durch Andocken des Stils angeben.  
  
 Während der Entwicklung verwalteter Toolfenster für das Tool register Fenster durch Hinzufügen von Attributen zu Quellcode, und das RegPkg.exe\-Hilfsprogramm in der resultierenden Assembly anschließend ausführen.  Weitere Informationen finden Sie unter [Registrieren ein Toolfenster](../extensibility/registering-a-tool-window.md).  
  
## Nicht verwaltete Tool\-Fenster\-Anbieter registrieren  
 Nicht verwaltete Anbieter müssen mit [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Toolfenster im Toolfenster der Systemregistrierung registrieren.  Im Folgenden .reg\-Datei fragment zeigt, wie ein dynamisches Toolfenster registriert sein könnte:  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\<version number>\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}]  
@="{01069cdd-95ce-4620-ac21-ddff6c57f012}"  
"Name"="Microsoft.Samples.VisualStudio.IDE.ToolWindow.DynamicWindowPane"  
"Float"="250, 250, 410, 430"  
"DontForceCreate"=dword:00000001  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}\Visibility]  
"{f1536ef8-92ec-443c-9ed7-fdadf150da82}"=dword:00000000  
```  
  
 In der ersten Schlüssel im Beispiel oben wurde Versionsnummer der Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], z. B. 7.1 oder 8.0, der Unterschlüssel {f0e1e9a1\-9860\-484d\-ad5d\-367d79aabf55} ist die GUID des fensterbereichs Tool \(DynamicWindowPane\), und der Standardwert " {} " ist die GUID 01069cdd\-95ce\-4620\-ac21\-ddff6c57f012 VSPackages, das das Toolfenster bereitstellt.  Eine Erläuterung der Gleitkomma\- und DontForceCreate\-Unterschlüssel finden Sie unter [Tool\-Fenster Anzeigekonfiguration](../extensibility/tool-window-display-configuration.md).  
  
 Die zweite optionale Schlüssel Toolfenster \\ Sichtbarkeit, gibt die GUID der Befehle an, die das Toolfenster sichtbar gemacht werden müssen.  In diesem Fall gibt es keine angegebenen Befehle.  Weitere Informationen finden Sie unter [Tool\-Fenster Anzeigekonfiguration](../extensibility/tool-window-display-configuration.md).  
  
## Siehe auch  
 [Grundlegendes zu VSPackages](../misc/vspackage-essentials.md)