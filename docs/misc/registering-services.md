---
title: "Registrieren von Diensten | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Dienste, Registrieren"
ms.assetid: c4ebac40-0374-4dda-948e-06fdda0e9c81
caps.latest.revision: 8
caps.handback.revision: 8
manager: "douge"
---
# Registrieren von Diensten
Ein Dienstanbieter muss seine globalen Dienste mit [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] registrieren, um das bedarfsgesteuerte Laden zu unterstützen.  
  
 Während der Entwicklung registrieren Anbieter von verwalteten Diensten entsprechende Dienste und Dienstüberschreibungen durch Hinzufügen von Attributen zum Quellcode für Pakete. Anschließend werden die Pakete in der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-IDE erstellt. Dadurch wird das Dienstprogramm „RegPkg.exe“ für die sich ergebende Assembly ausgeführt, dann das Paket registriert und für die Bereitstellung vorbereitet. Weitere Informationen finden Sie unter [Gewusst wie: Registrieren von Diensten](../misc/how-to-register-a-service.md).  
  
 Anbieter nicht verwalteter Dienste müssen die von ihnen bereitgestellten Dienste mit [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] im Abschnitt für Dienste oder Dienstüberschreibungen in der Systemregistrierung registrieren. Das folgende Fragment einer REG\-Datei zeigt, wie der Dienst, SVsTextManager, registriert werden kann:  
  
```  
[HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}] @="{F5E7E720-1401-11d1-883B-0000F87579D2}" "Name"="SVsTextManager"  
```  
  
 Im obigen Beispiel ist die Versionsnummer die Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], z. B. 7.1 oder 8.0, der Schlüssel {F5E7E71D\-1401\-11d1\-883B\-0000F87579D2} ist die Dienst\-ID \(SID\) des Diensts \(SVsTextManager\) und der Standardwert {F5E7E720\-1401\-11d1\-883B\-0000F87579D2} ist die Paket\-GUID des Textmanager\-VSPackage, das den Dienst bereitstellt.  
  
## Remotedienste und Hintergrundthreads  
 Von Ihnen bereitgestellte Dienste sind nicht automatisch remote oder für Hintergrundthreads verfügbar. Sie müssen eine Typbibliothek erstellen und registrieren, um die Dienste zur Verfügung zu stellen.  
  
 Sie können Ihre Typbibliothek über nicht verwaltetem Code, der die Visual Studio Library \(VSL\) verwendet, auf die folgende Weise registrieren:  
  
```  
#define VSL_REGISTER_TYPE_LIB TRUE #include <VSLPackageDllEntryPoints.cpp>  
```  
  
 Über verwalteten Code können Sie wie folgt einen Postbuildschritt hinzufügen:  
  
```  
regasm /tlb MyAssembly.dll  
```  
  
## Siehe auch  
 [Verwendung und Bereitstellung von Diensten](../extensibility/using-and-providing-services.md)   
 [Service – Grundlagen](../extensibility/internals/service-essentials.md)