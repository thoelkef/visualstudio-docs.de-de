---
title: Neuigkeiten in der Quellcodeverwaltung
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 31b55c57f47f25814eff24f13bcf91408468d0f4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200954"
---
# <a name="what39s-new-in-source-control-in-visual-studio-2015"></a>Neues in der Quell Code Verwaltung in Visual Studio 2015&#39;

[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] können Sie eine tief integrierte Quell Code Verwaltungs Lösung bereitstellen, indem Sie ein Quellcodeverwaltungs-VSPackage implementieren. In diesem Abschnitt werden die Features der Quellcodeverwaltungs-VSPackages beschrieben und eine Übersicht über die Implementierungs Schritte bereitstellt.  
  
## <a name="the-source-control-vspackage"></a>Das VSPackage der Quell Code Verwaltung  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] unterstützt zwei Typen von Quell Code Verwaltungslösungen. In allen Versionen von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] können Sie weiterhin ein API-basiertes Plug-in für die Quellcodeverwaltungs-Plug-ins integrieren. Sie können auch ein VSPackage für die Quell Code Verwaltung erstellen, das einen Deep-Integration-Pfad bereitstellt, der [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] für Quell Code Verwaltungslösungen geeignet ist, die ein hohes Maß an Komplexität und Autonomie erfordern.  
  
 Ein VSPackage kann nahezu jede Art von Funktionalität hinzufügen [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Ein Quellcodeverwaltungs-VSPackage bietet ein vollständiges Quell Code Verwaltungs Feature für [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , von der Benutzeroberfläche, die dem Benutzer für die Back-End-Kommunikation mit dem Quell Code Verwaltungssystem angezeigt wird.  
  
 Zum Implementieren eines VSPackage für die Quell Code Verwaltung ist eine all-oder Nothing-Strategie erforderlich. Der Ersteller eines Quellcodeverwaltungs-VSPackages muss einen beträchtlichen Aufwand bei der Implementierung einer Reihe von Quell Code Verwaltungs Schnittstellen und neuen Benutzeroberflächen Elementen (Dialogfelder, Menüs und Symbolleisten) investieren, um die gesamte Funktionalität der Quell Code Verwaltung zu behandeln, sowie die Schnittstellen, die für die Integration mit einem Paket erforderlich sind [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 Die folgenden Schritte zeigen einen allgemeinen Überblick darüber, was zum Implementieren eines Quell Code Verwaltungs Pakets erforderlich ist. Weitere Informationen finden Sie unter [Erstellen eines Quellcodeverwaltungs-VSPackages](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
1. Erstellen Sie ein VSPackage, das einen privaten Quell Code Verwaltungsdienst anbietet.  
  
2. Implementieren Sie die Schnittstellen in den auf die Quell Code Verwaltung bezogenen Diensten, die von angeboten werden [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (z <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> . b. die-Schnittstelle und die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> Schnittstelle).  
  
3. Registrieren Sie das VSPackage für die Quell Code Verwaltung.  
  
4. Implementieren Sie alle Benutzeroberflächen der Quell Code Verwaltung, einschließlich Menü Elemente, Dialogfeldern, Symbolleisten und Kontextmenüs.  
  
5. Alle Ereignisse in Zusammenhang mit der Quell Code Verwaltung werden an das vsackage der Quell Code Verwaltung übermittelt, wenn es aktiv ist und von Ihrem VSPackage behandelt werden muss.  
  
6. Das VSPackage der Quell Code Verwaltung muss auf Ereignisse lauschen, wie z. b. die, die die-Schnittstelle implementieren, und das nach <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> Verfolgen von Project Document (TPD)-Ereignissen (wie von der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> Schnittstelle implementiert) und das  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [Übersicht über](../../extensibility/internals/source-control-integration-overview.md)   
 [Erstellen eines Quellcodeverwaltungs-VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)
