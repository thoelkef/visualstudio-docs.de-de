---
title: Beitrag zum Automatisierungs Modell | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c84ea078f9b7c1268b765111cc400f6e51b783f1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196998"
---
# <a name="contributing-to-the-automation-model"></a>Mitwirken am Automatisierungsmodell
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio bietet eine Reihe von Automatisierungs Schnittstellen für die Anpassung der Umgebung. Das Automatisierungs Modell ist das Objektmodell, mit dem Endbenutzer Visual Studio-Add-Ins und-Erweiterungen erstellen können.  
  
 Außerdem ist es für Sie als VSPackage-Entwickler geeignet, zum Automatisierungs Modell beizutragen. auf diese Weise ermöglichen Sie Endbenutzern des VSPackages das Erstellen von Add-Ins und bieten im Allgemeinen ein konsistentes Benutzer Modell, wenn Sie Ihr VSPackage in verwenden [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 Um die Endbenutzer Leistung konsistent zu gestalten, können Sie beim Entwerfen des VSPackages eine Reihe von Richtlinien befolgen, damit das Automatisierungs Modell für Ihr VSPackage den Ideen in folgt [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Übersicht über das Automatisierungsmodell](../../extensibility/internals/automation-model-overview.md)  
 Definiert das Automatisierungs Modell als Verwandte Gruppen von Objekten, die die wichtigsten Facetten der allgemeinen Umgebung steuern. Diese Gruppe von Objekten wird in einem Diagramm des Automatisierungs Modells dargestellt.  
  
 [Bereitstellen von Automatisierung für VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md)  
 Erläutert die zwei Hauptmethoden zum Bereitstellen von Automatisierung für Ihr VSPackage.  
  
 [Verfügbarmachen von Projektobjekten](../../extensibility/internals/exposing-project-objects.md)  
 Enthält Schritt-für-Schritt-Anleitungen zum Erstellen von VSPackage-spezifischen Objekten.  
  
 [Projektmodellierung](../../extensibility/internals/project-modeling.md)  
 Erläutert die Standard Projekt Objekte, die zum Erstellen der Automatisierung für den neuen Projekttyp erforderlich sind, und veranschaulicht den Pfad, dem die Projektautomatisierung folgt. Dieses Thema enthält auch Auflistungen von Deklarationen und Implementierungen für-Klassen.  
  
 [Verfügbarmachen von Ereignissen](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)  
 Enthält Schritt-für-Schritt-Anleitungen zum Erstellen von Ereignissen für das Automatisierungs Modell.  
  
 [Automatisierungsunterstützung für Optionsseiten](../../extensibility/internals/automation-support-for-options-pages.md)  
 Beschreibt, wie ein Automatisierungs Objekt zurückgegeben wird, um Eigenschaften des Dialog Felds benutzerdefinierte **Optionen** für das VSPackage im **Tool** Menü durch Erweiterung des-Objekts zu unterstützen `DTE.Properties` .  
  
 [Bereitstellen von Automatisierung für Code](../../extensibility/internals/providing-automation-for-code.md)  
 Erläutert, dass das Erstellen eines Automatisierungs Modells für Ihren Code nicht erforderlich ist. In diesem Thema wird jedoch ein Link bereitgestellt, der aufschlussreiche Informationen zu Code Modellen bereitstellt.  
  
 [Gewusst wie: Bereitstellen von Automatisierung für Fenster](../../extensibility/internals/how-to-provide-automation-for-windows.md)  
 Erläutert, dass das Bereitstellen von Automatisierung eine gute Idee ist, wenn Sie Automation-Objekte in einem Fenster verfügbar machen möchten und die Umgebung nicht bereits ein vorgefertigte Automatisierungs Objekt bereitstellt. Erläutert die Automatisierung für Tool Fenster und Dokument Fenster.  
  
 [Verwenden des Automatisierungsmodells](../../extensibility/internals/using-the-automation-model.md)  
 Bietet zwei Codebeispiele, die zeigen, wie ein automatisierungsconsumer die anfänglichen Project Automation-Objekte abruft.  
  
 [Automatisierung für Konfigurations- und SelectedItem-Objekte](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)  
 Enthält Informationen zur Automatisierung für Konfigurationsoptionen und zur Automatisierung ausgewählter Elemente.  
  
## <a name="reference"></a>Verweis  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
 Enthält ein Codebeispiel, das zeigt, wie ein VSPackage an dem DTE-Automatisierungs Objektmodell teilnimmt. Listet Parameter, Rückgabewerte und ausgewählte Hinweise auf.  
  
## <a name="related-sections"></a>Verwandte Abschnitte
