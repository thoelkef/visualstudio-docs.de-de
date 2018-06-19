---
title: Zum Automatisierungsmodell beitragen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8333ed5c107f7f62e736ccd62e1b79723b5eb8f4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130517"
---
# <a name="contributing-to-the-automation-model"></a>Das Automatisierungsmodell beitragen.
Visual Studio bietet einen Satz von Automatisierungsschnittstellen zum Anpassen der umgebungs. Das Automatisierungsmodell ist das Objektmodell, das Endbenutzer zum Erstellen von Visual Studio-add-ins und -Erweiterungen aktiviert.  
  
 Darüber hinaus ist es für Sie geeignet als VSPackage-Entwickler, die zum Automatisierungsmodell beitragen. auf diese Weise können Sie Endbenutzer Ihres VSPackage-add-ins zu erstellen und Bereitstellen in der Regel eine konsistente benutzerumgebung Modell aus, wenn sie Ihr VSPackage in verwenden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Um der Endbenutzer auftreten konsistent zu machen, können Sie einen Satz von Richtlinien befolgen, wie Sie das VSPackage so entwerfen, dass das Automatisierungsmodell für Ihr VSPackage Ideen in folgt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Übersicht über das Automatisierungsmodell](../../extensibility/internals/automation-model-overview.md)  
 Definiert das Automatisierungsmodell eine verbundene Gruppen von Objekten, die wichtigsten Aspekte der allgemeinen Umgebung steuern. Dieser Satz von Objekten ist in einem Diagramm des Automatisierungsmodells abgebildet.  
  
 [Bereitstellen von Automatisierung für VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md)  
 Erläutert die zwei Hauptmethoden, um Automatisierung für Ihr VSPackage bereitzustellen.  
  
 [Verfügbarmachen von Projektobjekten](../../extensibility/internals/exposing-project-objects.md)  
 Enthält schrittweise Anweisungen zum Erstellen des VSPackage-Objekten.  
  
 [Projektmodellierung](../../extensibility/internals/project-modeling.md)  
 Erläutert, die standard-Projekt-Objekte, die zum Erstellen von Automation für den neuen Projekttyp erforderlich sind, und zeigt den Pfad, den Project Automation folgt. Dieses Thema enthält auch Angebote von Deklarationen und Implementierung für Klassen.  
  
 [Ereignisse verfügbar machen](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)  
 Bietet eine schrittweise Anleitung zum Erstellen von Ereignissen für das Automatisierungsmodell.  
  
 [Automatisierungsunterstützung für Optionsseiten](../../extensibility/internals/automation-support-for-options-pages.md)  
 Beschreibt, wie ein Automatisierungsobjekt zurückgegeben, für die Eigenschaften eines VSPackage unterstützen benutzerdefinierte's **Optionen** Dialogfeld auf die **Tool** Menü durch die Erweiterung der `DTE.Properties` Objekt.  
  
 [Bereitstellen von Automatisierung für Code](../../extensibility/internals/providing-automation-for-code.md)  
 Erläutert, dass ein Automatisierungsmodell für Ihren Code erstellen nicht erforderlich ist. Allerdings wird ein Link in diesem Thema bereitgestellt, die in Codemodelle erkenntnisreiche Informationen bereitstellt.  
  
 [Gewusst wie: Bereitstellen von Automatisierung für Fenster](../../extensibility/internals/how-to-provide-automation-for-windows.md)  
 Erläutert, dass automatisierte eine gute Idee, ist wenn Automatisierungsobjekten in einem Fenster verfügbar machen möchten, und die Umgebung keine bereits eine vorgefertigte Automatisierungsobjekt bietet. Erläutert die Automatisierung für Toolfenster und Dokumentfenster an.  
  
 [Verwenden des Automatisierungsmodells](../../extensibility/internals/using-the-automation-model.md)  
 Bietet zwei Codebeispielen, die veranschaulichen, wie ein Consumer Automation das ursprüngliche Projekt Automatisierungsobjekte erhält.  
  
 [Automatisierung für Konfigurations- und SelectedItem-Objekte](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)  
 Enthält Informationen über die Automatisierung für Konfigurationsoptionen und Automatisierung für ausgewählte Elemente.  
  
## <a name="reference"></a>Referenz  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
 Enthält ein Codebeispiel, das zeigt, wie eine VSPackage das DTE-Automatisierungsobjektmodell beteiligt. Listet Parameter und Rückgabewerte ausgewählten "Hinweise".  
  
## <a name="related-sections"></a>Verwandte Abschnitte