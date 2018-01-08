---
title: Source Control VSPackage Entwurfselemente | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control packages, design elements
ms.assetid: edd3f2ff-ca32-4465-8ace-4330493b67bb
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 234346aba360d70d3bbc673067d2634a5112d0f6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="source-control-vspackage-design-elements"></a>Source Control VSPackage Entwurfselemente
Die Themen in diesem Abschnitt beschreiben die Struktur der quellcodeverwaltung, VSPackage, für die enge Integration implementieren muss. Zudem werden die Schnittstellen aufgelistet und können Dienste, die die Quelle VSPackage steuern, implementieren und die Schnittstellen und Dienste können von anderen Datenquellen-Steuerelements VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Komponenten zur Unterstützung der seine Quelle zu steuern, Modell- und Funktionalität.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [VSPackage-Struktur](../../extensibility/internals/vspackage-structure-source-control-vspackage.md)  
 Definiert die Struktur des Datenquellen-Steuerelements VSPackage.  
  
 [Verknüpfte Dienste und Schnittstellen](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)  
 Steuerelement-Schnittstellen paketbezogene und Dienste aufgelistet.  
  
 [Bereitgestellten Dienste](../../extensibility/internals/services-provided-source-control-vspackage.md)  
 Beschreibt die quellcodeverwaltungsdienst, die von der quellcodeverwaltung VSPackage bereitgestellt.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Erstellen eines Quellcodeverwaltungs-VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)  
 Erläutert, wie ein Datenquellen-Steuerelement VSPackage zu erstellen, die nicht nur Quellcodeverwaltungsfunktion bereitstellt, sondern dienen zum Anpassen der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] quellcodeverwaltung UI.