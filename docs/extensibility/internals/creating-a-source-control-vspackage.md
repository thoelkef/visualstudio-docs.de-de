---
title: Erstellen eines Quellcodeverwaltungs-VSPackages | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 278f06376ede2ceb26ccc6ed31d7f4666a0882c0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54936631"
---
# <a name="create-a-source-control-vspackage"></a>Erstellen eines Quellcodeverwaltungs-VSPackage
Diese Dokumentation enthält Links zu der Architekturübersicht des ein Source-Control-Paket integriert [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], die API, die durch die Schnittstellen implementiert werden und die Dienste zur Nutzung definiert wird, und ein Beispiel, das veranschaulicht, eine einfache Quelle Steuern Sie die paketimplementierung.  
  
 Sie können mit der quellcodeverwaltung VSPackage, einen enge Integration Pfad für die quellcodeverwaltung für die Integration erstellen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Dadurch werden das Paket, das Standard-Datenquellen-Steuerelement von gehosteten UI umgehen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], reagieren auf Source-Control-Anforderungen aus dem Projektsystem und interagieren mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Komponenten wie z. B. **Projektmappen-Explorer**. Die [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] können [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] einen Mechanismus für die ein VSPackage zu erstellen, die integriert werden können Partner [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mithilfe eines Dienstmodells.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Erste Schritte](../../extensibility/internals/getting-started-with-source-control-vspackages.md)  
 Erläutert das Quellcodeverwaltungspaket, die eine erweiterte Alternative zum das Quellcodeverwaltungs-Plug-In für die Implementierung von Funktionen in quellcodeverwaltung ist [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Architektur](../../extensibility/internals/source-control-vspackage-architecture.md)  
 Zeigt ein Diagramm und erläutert die Komponenten ein Quellcode-Verwaltungspaket.  
  
 [Features](../../extensibility/internals/source-control-vspackage-features.md)  
 Beschreibt die verschiedenen Funktionen ein Quellcode-Verwaltungspaket.  
  
 [Entwurfselemente](../../extensibility/internals/source-control-vspackage-design-elements.md)  
 Beschreibt die Struktur des VSPackage, die ein Quellcode-Verwaltungspaket für die Tiefe Integration implementieren müssen.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Erstellen eines Quellcodeverwaltungs-Plug-in](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Erläutert, wie ein Quellcodeverwaltungs-Plug-in erstellen, die Quellcodeverwaltungsfunktionen in stellt das [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Source Control-Benutzeroberfläche (UI).  
  
 [Datenquellen-Steuerelement](../../extensibility/internals/source-control.md)  
 Erläutert die Optionen zum Implementieren von Datenquellen-Steuerelement als eine integrierte Funktion von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].
