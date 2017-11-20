---
title: Erstellen eines Source Control VSPackage | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4c3d414f1fcf6a7f4cd4155eb04e3696fb39740a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="creating-a-source-control-vspackage"></a>Erstellen eines Source Control VSPackage
Diese Dokumentation enthält Links zu den Architekturübersicht über eine quellcodeverwaltung Paket integriert [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], die API, die durch die Schnittstellen implementiert werden und die Dienste zu konsumierende definiert ist, und ein Beispiel, das veranschaulicht eine einfache Quelle Steuern Sie die paketimplementierung.  
  
 Ein VSPackage-quellcodeverwaltung, können Sie einen umfassende Integration Pfad für die quellcodeverwaltung für die Integration erstellen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Dadurch werden das Paket der Standard-Datenquellen-Steuerelements von gehosteten UI umgehen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], reagieren auf Quelle steueranforderungen aus dem Projektsystem und interagieren mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Verwaltungskomponenten wie **Projektmappen-Explorer**. Die [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Spornt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] einen Mechanismus für ein VSPackage erstellen, die mit integrieren können Partner [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mithilfe eines Dienstmodells.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Erste Schritte](../../extensibility/internals/getting-started-with-source-control-vspackages.md)  
 Erläutert das Quellcodeverwaltungspaket, das eine erweiterte Alternative zu den Datenquellen-Steuerelement-Plug-In für die Implementierung von Funktionen der quellcodeverwaltung in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Architektur](../../extensibility/internals/source-control-vspackage-architecture.md)  
 Zeigt ein Diagramm und erläutert die Komponenten einer Source Control-Paket.  
  
 [Funktionen](../../extensibility/internals/source-control-vspackage-features.md)  
 Beschreibt die verschiedenen Funktionen von einem Steuerelement Quellpaket.  
  
 [Entwurfselemente](../../extensibility/internals/source-control-vspackage-design-elements.md)  
 Beschreibt die Struktur des VSPackage, die ein Steuerelement Quellpaket für umfassende Integration implementieren müssen.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Erstellen eines Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Erläutert, wie ein Quellcodeverwaltungs-Plug-in erstellen, die Quellcodeverwaltungsfunktion in liefert die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Quelle Steuerelement-Benutzeroberfläche (UI).  
  
 [Quellcodeverwaltung](../../extensibility/internals/source-control.md)  
 Erläutert die Optionen für die Implementierung von Datenquellen-Steuerelements als eine integrierte Funktion von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].