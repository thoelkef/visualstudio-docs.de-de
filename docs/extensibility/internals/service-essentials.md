---
title: "Service – Grundlagen | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Dienste, essentials"
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Service – Grundlagen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ein Dienst ist ein Vertrag zwischen zwei VSPackages. Ein VSPackage bietet einen bestimmten Satz von Schnittstellen für einen anderen VSPackage nutzen.[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ist selbst eine Auflistung von VSPackages, die Dienste, die andere VSPackages bereitstellt.  
  
 Sie können z. B. die SVsActivityLog\-Dienst verwenden, beim Abrufen einer IVsActivityLog\-Schnittstelle, die Sie verwenden können, um in Aktivitätsprotokoll schreiben. Weitere Informationen finden Sie unter [Gewusst wie: Verwenden Sie das Aktivitätsprotokoll](../../extensibility/how-to-use-the-activity-log.md).  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Außerdem bietet einige integrierte Dienste, die nicht registriert werden. VSPackages können integrierte oder andere Dienste ersetzen, indem Sie eine Außerkraftsetzung Dienst bereitstellen. Nur ein Dienst Außerkraftsetzung ist für jeden Dienst zulässig.  
  
 Dienste verfügen über keine Erkennbarkeit. Aus diesem Grund benötigen Sie die Dienst\-ID \(SID\) eines Diensts, die Sie nutzen möchten, und Sie müssen wissen, welche Schnittstellen bietet. Die Referenzdokumentation für den Dienst enthält diese Informationen.  
  
-   VSPackages, die Dienste bereitstellen, werden als Dienstanbieter bezeichnet.  
  
-   Dienste, die andere VSPackages bereitgestellt werden, werden als globale Dienste bezeichnet.  
  
-   Dienste, die stehen nur für die VSPackage, das sie implementiert, oder um ein Objekt erstellt wird, werden lokale Dienste bezeichnet.  
  
-   Dienste, die integrierte Dienste oder Dienste von anderen Paketen ersetzen heißen Diensten überschrieben.  
  
-   Dienste oder Dienst überschreibt, werden bei Bedarf geladen, d. h. der Dienstanbieter geladen wird, wenn der Dienst bereitgestellten durch eine andere VSPackage angefordert wird.  
  
-   Um bei Bedarf laden zu unterstützen, ein Dienstanbieter registriert seine globale Dienste mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Weitere Informationen finden Sie unter [Registrieren von Diensten](../../misc/registering-services.md).  
  
-   Nachdem Sie einen Dienst abzurufen, verwenden Sie [QueryInterface](/visual-cpp/atl/queryinterface) \(nicht verwaltetem Code\) oder umwandeln \(verwalteter Code\) die gewünschte Schnittstelle, z. B. abrufen:  
  
    ```vb#  
    TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
    ```  
  
    ```c#  
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
  
    ```  
  
-   Verwalteter Code bezieht sich auf einen Dienst anhand des Typs, nicht verwalteter Code eines Diensts anhand seiner GUID bezeichnet.  
  
-   Wenn [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] lädt ein VSPackage, übergibt er einen Dienstanbieter an dem VSPackage der VSPackage\-Zugriff auf globale Dienste gewähren. Dies wird als VSPackage "Positionierung" bezeichnet.  
  
-   VSPackages kann Dienstanbieter für die Objekte, die sie erstellen. Ein Formular kann z. B. eine Anforderung für einen Dienst Farbe auf den Rahmen, der der Anforderung übergeben werden kann senden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   Verwaltete Objekte, die tief geschachtelt oder nicht platziert, ruft <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> für direkten Zugriff auf globale Dienste. Weitere Informationen finden Sie unter [Gewusst wie: Verwenden von GetGlobalService](../../misc/how-to-use-getglobalservice.md).  
  
## Siehe auch  
 [Liste der verfügbaren Dienste](../../extensibility/internals/list-of-available-services.md)   
 [Verwendung und Bereitstellung von Diensten](../../extensibility/using-and-providing-services.md)   
 [Umwandlung und Typkonvertierungen](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)   
 [Umwandlung von Typen](/visual-cpp/cpp/casting)