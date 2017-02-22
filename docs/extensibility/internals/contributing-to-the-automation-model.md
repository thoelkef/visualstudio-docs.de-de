---
title: "Das Automatisierungsmodell beitragen. | Microsoft Docs"
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
  - "Automatisierung [Visual Studio SDK]"
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# Das Automatisierungsmodell beitragen.
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Visual Studio bietet eine Reihe von Automatisierungsschnittstellen für die Umgebung anzupassen. Das Automatisierungsmodell wird das Objektmodell, mit dem Endbenutzer Visual Studio\-add\-ins und \-Erweiterungen erstellen kann.  
  
 Darüber hinaus ist es für Sie als Entwickler VSPackage zur Teilnahme an das Automatisierungsmodell geeignet; auf diese Weise können Sie Endbenutzer von Ihr VSPackage\-add\-ins erstellen und im Allgemeinen ein einheitliches Modell Benutzererlebnis bei Verwendung das VSPackage in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Um die endbenutzererfahrung konsistent zu machen, können Sie eine Reihe von Richtlinien folgen, wie Sie Ihr VSPackage so entwerfen, dass das Automatisierungsmodell für das VSPackage Ideen in folgt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## In diesem Abschnitt  
 [Übersicht über die Benutzeroberflächenautomatisierungs\-Modell](../../extensibility/internals/automation-model-overview.md)  
 Definiert das Automatisierungsmodell eine miteinander verbundene Gruppen von Objekten, die wichtigsten Aspekte der allgemeinen Umgebung steuern. Dieser Satz von Objekten ist in einem Diagramm des Automatisierungsmodells abgebildet.  
  
 [Automatisierte für VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md)  
 Erläutert zwei Hauptmethoden zur Automatisierung für das VSPackage.  
  
 [Verfügbarmachen von Projektobjekten](../../extensibility/internals/exposing-project-objects.md)  
 Bietet eine schrittweise Anleitung zum Erstellen von VSPackage\-Objekten.  
  
 [Projekt\-Modellierung](../../extensibility/internals/project-modeling.md)  
 Erläutert die standard\-Projekt\-Objekte, die zum Erstellen von Automation für den neuen Projekttyp erforderlich sind, und zeigt den Pfad, den Project\-Automatisierung folgt. Dieses Thema enthält auch Angebote von Deklarationen und Implementierung für Klassen.  
  
 [Das Offenlegen von Ereignissen](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)  
 Bietet eine schrittweise Anleitung zum Erstellen von Ereignissen für die Benutzeroberflächenautomatisierungs\-Modell.  
  
 [Benutzeroberflächenautomatisierungs\-Unterstützung für Optionen \(Seiten\)](../../extensibility/internals/automation-support-for-options-pages.md)  
 Beschreibt, wie ein Automatisierungsobjekt zurückgegeben wird, unterstützten Eigenschaften von VSPackages benutzerdefinierte dann den **Optionen** im Dialogfeld auf die **Tool** Menü durch Erweitern der `DTE.Properties` Objekt.  
  
 [Automatisierte für Code](../../extensibility/internals/providing-automation-for-code.md)  
 Erklärt, erstellen ein Automatisierungsmodell für Ihren Code nicht erforderlich ist. Allerdings wird ein Link in diesem Thema bereitgestellt, die in Codemodelle aufschlussreiche Informationen bereitstellt.  
  
 [Gewusst wie: Bereitstellen von Automatisierung für Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md)  
 Erklärt, dass automatisierte eine gute Idee, ist wenn Automatisierungsobjekten in einem Fenster verfügbar machen möchten, und die Umgebung keine bereits eine vorgefertigte Automatisierungsobjekt bietet. Beschreibt die Automatisierung für Toolfenstern und Dokumentfenstern.  
  
 [Verwenden des Automatisierungs\-Modells](../../extensibility/internals/using-the-automation-model.md)  
 Enthält zwei Codebeispiele, die zeigen, wie ein Automation\-Consumer das ursprüngliche Projekt Automatisierungsobjekte erhält.  
  
 [Automatisierung für die Konfiguration und SelectedItem\-Objekte](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)  
 Enthält Informationen über die Automatisierung für Konfigurationsoptionen und Automatisierung für ausgewählte Elemente.  
  
## Referenz  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
 Enthält ein Codebeispiel, das zeigt, wie ein VSPackage an das DTE\-Automatisierungsobjektmodell teilnimmt. Listen\-Parameter, Rückgabewerte und ausgewählte hinweisen.  
  
## Verwandte Abschnitte