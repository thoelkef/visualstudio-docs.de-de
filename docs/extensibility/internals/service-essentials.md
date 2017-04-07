---
title: Essentials Service | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 8ff357d7ed3542a01cf8d98e36b9d0e99a122864
ms.lasthandoff: 04/05/2017

---
# <a name="service-essentials"></a>Dienst-Grundlagen
Ein Dienst ist ein Vertrag zwischen zwei VSPackages. Ein VSPackage bietet es sich um einen bestimmten Satz von Schnittstellen für einen anderen VSPackage zu nutzen. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ist selbst eine Auflistung von VSPackages, die Dienste, die andere VSPackages bereitstellt.  
  
 Sie können z. B. die SVsActivityLog-Dienst verwenden, beim Abrufen einer IVsActivityLog-Schnittstelle, die Sie, zum Schreiben in das Aktivitätsprotokoll verwenden können. Weitere Informationen finden Sie unter [Vorgehensweise: Verwenden Sie das Aktivitätsprotokoll](../../extensibility/how-to-use-the-activity-log.md).  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]bietet außerdem einige integrierte Dienste, die nicht registriert werden. VSPackages können integrierte oder andere Dienste ersetzen, indem Sie eine Außerkraftsetzung Dienst bereitstellen. Nur ein Dienst Außerkraftsetzung wird für jeden Dienst zulässig.  
  
 Dienste verfügen über keine gefunden werden können. Aus diesem Grund benötigen Sie die Dienst-ID (SID) eines Diensts, die Sie nutzen möchten, und Sie müssen wissen, welche Schnittstellen es bietet. Die Referenzdokumentation für den Dienst enthält diese Informationen.  
  
-   VSPackages, die Dienste bereitstellen, werden als Dienstanbieter bezeichnet.  
  
-   Dienste, die für andere VSPackages bereitgestellt werden, werden als globale Dienste bezeichnet.  
  
-   Dienste, die nur für das VSPackage, das sie implementiert, oder klicken Sie auf ein beliebiges Objekt erstellt, verfügbar sind, werden als lokale Dienste bezeichnet.  
  
-   Dienste, die integrierte Dienste oder Dienste von anderen Paketen zu ersetzen, werden als dienstüberschreibungen bezeichnet.  
  
-   Dienste oder dienstüberschreibungen, bei Bedarf geladen werden, d. h. der Dienstanbieter geladen wird, wenn der Dienst bietet ein von einem anderen VSPackage angefordert wird.  
  
-   Um eine bedarfsgesteuerte Laden zu unterstützen, registriert ein Dienstanbieter seine globalen Dienste mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Weitere Informationen finden Sie unter [Registrieren von Diensten](../../misc/registering-services.md).  
  
-   Verwenden Sie nach dem Erwerb eines Diensts [QueryInterface](/cpp/atl/queryinterface) (nicht verwaltetem Code) oder umwandeln (verwalteter Code) auf die gewünschte Schnittstelle zu erhalten, z. B.:  
  
    ```vb#  
    TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
    ```  
  
    ```c#  
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
  
    ```  
  
-   Verwalteter Code bezieht sich an einen Dienst anhand des Typs hingegen nicht verwalteter Code an einen Dienst durch ihre GUID verweist.  
  
-   Wenn [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] lädt ein VSPackage, übergibt es einen Dienstanbieter an dem VSPackage, um die VSPackage-Zugriff auf globale Dienste zu gewähren. Dies wird als "Positionierung" das VSPackage bezeichnet.  
  
-   VSPackages können Dienstanbieter für die Objekte erstellt werden. Z. B. ein Formular könnte eine Anforderung für einen Dienst für die Farbe an dessen Rahmen, der übergibt die Anforderung zum Senden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   Verwaltete Objekte, die tief verschachtelt sind, oder überhaupt nicht positioniert können aufgerufen werden <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>für direkten Zugriff auf globale Dienste.</xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> Weitere Informationen finden Sie unter [wie: Verwenden von GetGlobalService](../../misc/how-to-use-getglobalservice.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Liste der verfügbaren Dienste](../../extensibility/internals/list-of-available-services.md)   
 [Verwenden und die Bereitstellung von Diensten](../../extensibility/using-and-providing-services.md)   
 [Umwandlung und Typkonvertierungen](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)   
 [Umwandlung](/cpp/cpp/casting)
