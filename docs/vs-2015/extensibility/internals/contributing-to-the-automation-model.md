---
title: Mitwirken am Automatisierungsmodell | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 102a84781d033948490fb87e8b775f3b85ab61ba
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49268423"
---
# <a name="contributing-to-the-automation-model"></a>Mitwirken am Automatisierungsmodell
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio bietet eine Reihe von Automatisierungsschnittstellen für die Umgebung anzupassen. Das Automatisierungsmodell ist das Objektmodell, das Benutzer zum Erstellen von Visual Studio-add-ins und-Erweiterungen ermöglicht.  
  
 Darüber hinaus ist es für Sie geeignet als VSPackage-Entwickler zum Automatisierungsmodell beitragen. auf diese Weise können Sie Endbenutzer, die von einem VSPackage-add-ins erstellen und Bereitstellen in der Regel eine konsistente benutzererfahrung Modell aus, wenn sie Ihr VSPackage in verwenden [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 Um die endbenutzererfahrung konsistent zu machen, können Sie eine Reihe von Richtlinien befolgen, wie Sie das VSPackage so entwerfen, dass das Automatisierungsmodell für das VSPackage die Ideen folgt [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Übersicht über das Automatisierungsmodell](../../extensibility/internals/automation-model-overview.md)  
 Definiert das Automatisierungsmodell eine miteinander verbundene Gruppen von Objekten, die wesentliche Merkmale der gemeinsamen Umgebung zu steuern. Dieser Satz von Objekten ist in einem Diagramm des Automatisierungsmodells abgebildet.  
  
 [Bereitstellen von Automatisierung für VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md)  
 Beschreibt die zwei Hauptmethoden zum Bereitstellen von Automatisierung für Ihr VSPackage.  
  
 [Verfügbarmachen von Projektobjekten](../../extensibility/internals/exposing-project-objects.md)  
 Bietet schrittweise Anleitungen zum Erstellen von VSPackage-Objekten.  
  
 [Projektmodellierung](../../extensibility/internals/project-modeling.md)  
 Erläutert die standard-Projekt-Objekte, die zum Erstellen von Automation für den neuen Projekttyp erforderlich sind, und zeigt den Pfad für den Projekt-Automatisierung entspricht. Dieses Thema enthält auch Auflistungen von Deklarationen und Implementierung für Klassen.  
  
 [Verfügbarmachen von Ereignissen](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)  
 Bietet schrittweise Anleitungen zum Erstellen von Ereignissen für Ihr Automatisierungsmodell.  
  
 [Automatisierungsunterstützung für Optionsseiten](../../extensibility/internals/automation-support-for-options-pages.md)  
 Beschreibt, wie Sie ein Automatisierungsobjekt zurück, für die Eigenschaften von einem VSPackage unterstützt benutzerdefinierte ist **Optionen** Dialogfeld auf die **Tool** Menü durch die Erweiterung der `DTE.Properties` Objekt.  
  
 [Bereitstellen von Automatisierung für Code](../../extensibility/internals/providing-automation-for-code.md)  
 Erklärt, dass die Erstellung eines Automatisierungsmodells für Ihren Code nicht erforderlich ist. Allerdings wird ein Link in diesem Thema bereitgestellt, die aussagekräftige Informationen in Codemodelle enthält.  
  
 [Gewusst wie: Bereitstellen von Automatisierung für Fenster](../../extensibility/internals/how-to-provide-automation-for-windows.md)  
 Erklärt, dass das Bereitstellen von Automatisierung ist eine gute Idee, wann immer Sie-Automatisierungsobjekte in einem Fenster zur Verfügung stellen möchten, und die Umgebung eine vorgefertigte Automatisierungsobjekt keine bereits bietet. Erläutert die Automatisierung für Toolfenster und Dokumentfenster.  
  
 [Verwenden des Automatisierungsmodells](../../extensibility/internals/using-the-automation-model.md)  
 Enthält zwei Codebeispiele, die zeigen, wie ein automatisierungsbenutzer das ursprüngliche Projekt Automatisierungsobjekte erhält.  
  
 [Automatisierung für Konfigurations- und SelectedItem-Objekte](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)  
 Enthält Informationen über die Automatisierung für Konfigurationsoptionen und Automatisierung für ausgewählte Elemente.  
  
## <a name="reference"></a>Referenz  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
 Enthält ein Codebeispiel, das zeigt, wie eine VSPackage das DTE-Automatisierungsobjektmodell teilnimmt. Listen-Parameter, Rückgabewerte und ausgewählte "Hinweise".  
  
## <a name="related-sections"></a>Verwandte Abschnitte

