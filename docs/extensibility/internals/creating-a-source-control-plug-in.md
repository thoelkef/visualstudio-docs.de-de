---
title: Erstellen ein Quellcodeverwaltungs-Plug-in | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: c7e69fa4-150e-469a-a6fc-fa1260bdbb07
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 04c6125004aaf2740b54acdce91bef032647c6e5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31127855"
---
# <a name="creating-a-source-control-plug-in"></a>Erstellen ein Quellcodeverwaltungs-Plug-in
Das Visual Studio SDK enthält Ressourcen, die Ihnen ermöglichen, Quelle Steuerungsfunktionen für das Hinzufügen der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung (IDE). Es können Sie alle Plug-in-DLL, der kompatibel mit der Quelle-Plug-in-API mit dem in dieser Dokumentation beschriebenen Schritte aus.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Erste Schritte](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)  
 Beschreibt, wie ein Quellcodeverwaltungs-Plug-in zu installieren, und hebt die derzeit verfügbaren Source Control-Plug-in-API-Versionen.  
  
 [Architektur](../../extensibility/internals/source-control-plug-in-architecture.md)  
 Wird mit einer Architekturdiagramm erläutert, die Integration von ein Quellcodeverwaltungs-Plug-in mit der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 [Testleitfaden für Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)  
 Enthält Hinweise dazu, wie Sie die Installation und Ausführung von ein Quellcodeverwaltungs-Plug-in zu testen.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Erstellen eines Quellcodeverwaltungs-VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)  
 Erläutert, wie ein Datenquellen-Steuerelement VSPackage zu erstellen, der nicht nur Quellcodeverwaltungsfunktion bereitstellt, aber ersetzt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] quellcodeverwaltung UI.  
  
 [Quellcodeverwaltungs-Plug-Ins](../../extensibility/source-control-plug-ins.md)  
 Bietet eine vollständige Liste aller Elemente in der Quelle Steuerelement-Plug-in-API.  
  
 [Quellcodeverwaltung](../../extensibility/internals/source-control.md)  
 Erläutert die Optionen für die Implementierung von Datenquellen-Steuerelements als eine integrierte Funktion von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].