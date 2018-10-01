---
title: Registrieren von Diensten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- services, registering
ms.assetid: c4ebac40-0374-4dda-948e-06fdda0e9c81
caps.latest.revision: 8
manager: douge
ms.openlocfilehash: f56c73bbb09c659a76083e511d79d487402477ac
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515722"
---
# <a name="registering-services"></a>Registrieren von Diensten
Um bedarfsgesteuerte Laden zu unterstützen, registrieren ein Dienstanbieter muss seine globalen Dienste mit [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 Während der Entwicklung registrieren Anbieter von verwalteten Diensten Dienste und dienstüberschreibungen durch Hinzufügen von Attributen auf den Quellcode für Pakete, und klicken Sie dann die Pakete erstellen, in der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE. Dadurch wird das Dienstprogramm „RegPkg.exe“ für die sich ergebende Assembly ausgeführt, dann das Paket registriert und für die Bereitstellung vorbereitet. Weitere Informationen finden Sie unter [Vorgehensweise: Registrieren von Diensten](../misc/how-to-register-a-service.md).  
  
 Nicht verwaltete Dienstanbieter müssen die Dienste, die sie bieten registrieren [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Abschnitt oder dienstüberschreibungen in den Diensten im Abschnitt der Registrierung des Systems. Das folgende Fragment einer REG-Datei zeigt, wie der Dienst, SVsTextManager, registriert werden kann:  
  
```  
[HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]  
@="{F5E7E720-1401-11d1-883B-0000F87579D2}"  
"Name"="SVsTextManager"  
```  
  
 Im obigen Beispiel ist die Versionsnummer die Version von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], z. B. 7.1 oder 8.0, der Schlüssel {F5E7E71D-1401-11d1-883B-0000F87579D2} ist die Dienst-ID (SID) der Dienst, SVsTextManager und den standardmäßigen Wert {} F5E7E720-1401-11D1-883B-0000F87579D2} ist die Paket-GUID des TextManager-VSPackage, das den Dienst bereitstellt.  
  
## <a name="remote-services-and-background-threads"></a>Remotedienste und Hintergrundthreads  
 Von Ihnen bereitgestellte Dienste sind nicht automatisch remote oder für Hintergrundthreads verfügbar. Sie müssen eine Typbibliothek erstellen und registrieren, um die Dienste zur Verfügung zu stellen.  
  
 Sie können Ihre Typbibliothek über nicht verwaltetem Code, der die Visual Studio Library (VSL) verwendet, auf die folgende Weise registrieren:  
  
```  
#define VSL_REGISTER_TYPE_LIB TRUE  
#include <VSLPackageDllEntryPoints.cpp>  
```  
  
 Über verwalteten Code können Sie wie folgt einen Postbuildschritt hinzufügen:  
  
```  
regasm /tlb MyAssembly.dll  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden und Bereitstellen von Diensten](../extensibility/using-and-providing-services.md)   
 [Dienstgrundlagen](../extensibility/internals/service-essentials.md)