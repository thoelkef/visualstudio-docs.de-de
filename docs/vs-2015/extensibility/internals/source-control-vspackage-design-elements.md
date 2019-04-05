---
title: Quellcode-Steuerelemente für die VSPackage-Design | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control packages, design elements
ms.assetid: edd3f2ff-ca32-4465-8ace-4330493b67bb
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 06cd4523f91c341029140764b31fbd0ee262d551
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58958949"
---
# <a name="source-control-vspackage-design-elements"></a>Entwurfselemente von Quellcodeverwaltungs-VSPackages
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die Themen in diesem Abschnitt beschreiben die Struktur der quellcodeverwaltung, die VSPackages, für die Tiefe Integration implementieren muss. Zudem werden die Schnittstellen aufgelistet und können Dienste, die Quelle VSPackage steuern, implementieren und die Schnittstellen und Dienste können von anderen das Quellcodeverwaltungs-VSPackage [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Komponenten zur Unterstützung ihrer Quelle zu steuern, Modell und Funktionen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [VSPackage-Struktur](../../extensibility/internals/vspackage-structure-source-control-vspackage.md)  
 Definiert die Struktur des Datenquellen-Steuerelements VSPackage.  
  
 [Verwandte Dienste und Schnittstellen](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)  
 Liste von Steuerelement paketbezogene Quellschnittstellen und Diensten.  
  
 [Bereitgestellte Dienste](../../extensibility/internals/services-provided-source-control-vspackage.md)  
 Beschreibt den quellcodeverwaltungsdienst von das Quellcodeverwaltungs-VSPackage bereitgestellt.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Erstellen eines Quellcodeverwaltungs-VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)  
 Erläutert, wie ein Quellcodeverwaltungs-VSPackage zu erstellen, die nicht nur Quellcodeverwaltungsfunktionen bereitstellt, sondern dienen zum Anpassen der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Datenquellen-Steuerelement-Benutzeroberfläche.
