---
title: Service Essentials | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 90b16c9d7e7a762b6c1dac322ae9467b835476fd
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58956293"
---
# <a name="service-essentials"></a>Dienstgrundlagen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ein Dienst ist ein Vertrag zwischen zwei VSPackages. Ein VSPackage bietet es sich um einen bestimmten Satz von Schnittstellen für einen anderen VSPackage zu nutzen. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ist selbst eine Auflistung von VSPackages, die Dienste für andere VSPackages bereitstellt.  
  
 Sie können z. B. der SVsActivityLog-Dienst verwenden, beim Abrufen einer IVsActivityLog-Schnittstelle, die Sie zum Schreiben in das Aktivitätsprotokoll verwenden können. Weitere Informationen finden Sie unter [Vorgehensweise: Verwenden des Aktivitätsprotokolls](../../extensibility/how-to-use-the-activity-log.md).  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] bietet außerdem einige integrierte Dienste, die nicht registriert sind. VSPackages können integrierte oder andere Dienste ersetzen Sie dies durch die Bereitstellung von einem Dienst außer Kraft setzen. Nur ein Dienst außer Kraft setzen, ist für jeden Dienst zulässig.  
  
 Dienste verfügen über keine ermittelbarkeit. Aus diesem Grund benötigen Sie die Dienst-ID (SID) eines Diensts, die Sie nutzen möchten, und Sie müssen wissen, welche Schnittstellen es bietet. Die Referenzdokumentation für den Dienst stellt diese Informationen bereit.  
  
-   VSPackages, die Dienste bereitstellen, werden als Dienstanbieter bezeichnet.  
  
-   Dienste, die anderen VSPackages bereitgestellt werden, werden als globale Dienste bezeichnet.  
  
-   Dienste, die nur für das VSPackage, das sie implementiert, oder auf ein beliebiges Objekt damit erstellten verfügbar sind, werden als lokale Dienste bezeichnet.  
  
-   Dienste, die integrierten Dienste oder Dienste von anderen Paketen zu ersetzen, werden als dienstüberschreibungen bezeichnet.  
  
-   Dienste oder dienstüberschreibungen, bei Bedarf geladen werden, die der Dienstanbieter ist, also geladen, wenn der bereitgestellte Dienst von einem anderen VSPackage angefordert wird.  
  
-   Um das bedarfsgesteuerte Laden zu unterstützen, registriert ein Dienstanbieter seine globalen Dienste mit [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Weitere Informationen finden Sie unter [Registrieren von Diensten](../../misc/registering-services.md).  
  
-   Verwenden Sie nach dem Erwerb eines Diensts [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) (nicht verwaltetem Code) oder umwandeln (verwalteter Code), um die gewünschte Schnittstelle, z. B. zu erhalten:  
  
    ```vb  
    TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
    ```  
  
    ```csharp  
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
  
    ```  
  
-   Verwalteter Code verweist auf einen Dienst anhand des Typs, auf, während an einen Dienst durch ihre GUID nicht verwalteter Code bezeichnet.  
  
-   Wenn [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] lädt ein VSPackage, übergibt einen Dienstanbieter für dem VSPackage die VSPackage-Zugriff auf globale Dienste gewähren. Dies wird als "Positionierung" VSPackage bezeichnet.  
  
-   VSPackages kann es sich um Dienstanbieter für die Objekte sein, die sie erstellen. Ein Formular könnte z. B. eine Anforderung für einen Dienst für die Farbe an die Rahmen, der der Anforderung übergeben kann senden [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
-   Verwaltete Objekte, die tief verschachtelt sind, oder überhaupt nicht positioniert können aufgerufen werden <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> für direkten Zugriff auf globale Dienste. Weitere Informationen finden Sie unter [Vorgehensweise: Verwenden von GetGlobalService](../../misc/how-to-use-getglobalservice.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Liste der verfügbaren Dienste](../../extensibility/internals/list-of-available-services.md)   
 [Verwenden und Bereitstellen von Diensten](../../extensibility/using-and-providing-services.md)   
 [Umwandlung und Typkonvertierungen](http://msdn.microsoft.com/library/568df58a-d292-4b55-93ba-601578722878)   
 [Umwandlung](http://msdn.microsoft.com/library/3dbeb06e-2f4b-4693-832d-624bc8ec95de)
