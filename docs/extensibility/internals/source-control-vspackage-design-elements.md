---
title: Source Control VSPackage Entwurfselemente | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control packages, design elements
ms.assetid: edd3f2ff-ca32-4465-8ace-4330493b67bb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: eb741a7dc7423c27baed2cd79476239f4e41a170
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
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