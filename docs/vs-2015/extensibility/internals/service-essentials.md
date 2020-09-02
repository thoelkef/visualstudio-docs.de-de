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
ms.openlocfilehash: 407dda2f203b7be20b19c0e296caa9ce1c95b32c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696077"
---
# <a name="service-essentials"></a>Dienstgrundlagen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ein Dienst ist ein Vertrag zwischen zwei VSPackages. Ein VSPackage stellt einen bestimmten Satz von Schnittstellen für ein anderes VSPackage bereit, das verwendet werden soll. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ist selbst eine Sammlung von VSPackages, die Dienste für andere VSPackages bereitstellt.  
  
 Beispielsweise können Sie den Dienst SVsActivityLog zum Abrufen einer IVsActivityLog-Schnittstelle verwenden, die Sie verwenden können, um in das Aktivitätsprotokoll zu schreiben. Weitere Informationen finden Sie unter Gewusst [wie: Verwenden des Aktivitäts Protokolls](../../extensibility/how-to-use-the-activity-log.md).  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] bietet auch einige integrierte Dienste, die nicht registriert sind. VSPackages können integrierte oder andere Dienste durch Bereitstellen einer Dienst Überschreibung ersetzen. Nur eine Dienst Außerkraftsetzung ist für einen beliebigen Dienst zulässig.  
  
 Dienste können nicht gefunden werden. Daher müssen Sie die Dienst Kennung (SID) eines dienstanzdienstaners kennen, den Sie verwenden möchten, und Sie müssen wissen, welche Schnittstellen Sie bereitstellt. Diese Informationen finden Sie in der Referenz Dokumentation für den-Dienst.  
  
- VSPackages, die Dienste bereitstellen, werden als Dienstanbieter bezeichnet.  
  
- Dienste, die für andere VSPackages bereitgestellt werden, werden als globale Dienste bezeichnet.  
  
- Dienste, die nur für das VSPackage, das Sie implementiert, oder für ein beliebiges Objekt verfügbar sind, werden als lokale Dienste bezeichnet.  
  
- Dienste, die integrierte Dienste oder Dienste ersetzen, die von anderen Paketen bereitgestellt werden, werden als Dienst Überschreibungen bezeichnet.  
  
- Dienste oder Dienst Überschreibungen werden bei Bedarf geladen, d. h., der Dienstanbieter wird geladen, wenn der bereitgestellte Dienst von einem anderen VSPackage angefordert wird.  
  
- Um das Bedarfs gesteuerte laden zu unterstützen, registriert ein Dienstanbieter seine globalen Dienste bei [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Weitere Informationen finden Sie unter [Registrieren von Diensten](../../misc/registering-services.md).  
  
- Nachdem Sie einen Dienst abgerufen haben, verwenden Sie [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) (nicht verwalteter Code) oder Umwandlungs (verwalteter Code), um die gewünschte Schnittstelle abzurufen, z. b.:  
  
    ```vb  
    TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
    ```  
  
    ```csharp  
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
  
    ```  
  
- Verwalteter Code bezieht sich auf einen Dienst über seinen Typ, wohingegen nicht verwalteter Code über seine GUID auf einen Dienst verweist.  
  
- Wenn [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ein VSPackage lädt, übergibt es einen Dienstanbieter an das VSPackage, um dem VSPackage Zugriff auf globale Dienste zu verschaffen. Dies wird als "siting" des VSPackage bezeichnet.  
  
- VSPackages können Dienstanbieter für die Objekte sein, die Sie erstellen. Beispielsweise kann ein Formular eine Anforderung für einen Farb Dienst an seinen Frame senden, der die Anforderung möglicherweise an übergibt [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
- Verwaltete Objekte, die tief geschachtelt sind oder überhaupt nicht positioniert sind, können <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> für den direkten Zugriff auf globale Dienste aufrufen. Weitere Informationen finden Sie unter Gewusst [wie: Verwenden von GetGlobalService](../../misc/how-to-use-getglobalservice.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Liste der verfügbaren Dienste](../../extensibility/internals/list-of-available-services.md)   
 [Verwenden von und Bereitstellen von Diensten](../../extensibility/using-and-providing-services.md)   
 [Umwandlung und Typkonvertierungen](https://msdn.microsoft.com/library/568df58a-d292-4b55-93ba-601578722878)   
 [Umwandlung](https://msdn.microsoft.com/library/3dbeb06e-2f4b-4693-832d-624bc8ec95de)
