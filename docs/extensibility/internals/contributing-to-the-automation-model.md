---
title: Beitrag zum Automatisierungsmodell | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d660edc740229c3e91b99e1f59eb37b4e9312098
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709269"
---
# <a name="contribute-to-the-automation-model"></a>Beitrag zum Automatisierungsmodell
Visual Studio bietet eine Reihe von Automatisierungsschnittstellen zum Anpassen der Umgebung. Das Automatisierungsmodell ist das Objektmodell, mit dem Endbenutzer Visual Studio-Add-Ins und -Erweiterungen erstellen können.

 Darüber hinaus ist es für Sie als VSPackage-Entwickler geeignet, zum Automatisierungsmodell beizutragen. Auf diese Weise ermöglichen Sie Endbenutzern Ihres VSPackage, Add-Ins zu erstellen und im Allgemeinen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]eine konsistente Benutzermodellerfahrung bereitzustellen, wenn sie Ihr VSPackage in verwenden.

 Um die Endbenutzererfahrung konsistent zu gestalten, können Sie beim Entwerfen Ihres VSPackage eine Reihe von Richtlinien [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]befolgen, sodass das Automatisierungsmodell für Ihr VSPackage den Ideen in folgt.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Übersicht über das Automatisierungsmodell](../../extensibility/internals/automation-model-overview.md)

 Definiert das Automatisierungsmodell als verwandte Objektgruppen, die wichtige Facetten der gemeinsamen Umgebung steuern. Dieser Satz von Objekten ist in einem Diagramm des Automatisierungsmodells abgebildet.

- [Automatisierung für VSPackages bereitstellen](../../extensibility/internals/providing-automation-for-vspackages.md)

 Erläutert die beiden wichtigsten Möglichkeiten zur Automatisierung Ihres VSPackage.

- [Stellen sie Projektobjekte zur Zeit](../../extensibility/internals/exposing-project-objects.md)

 Enthält schritt für Schritt Anweisungen zum Erstellen von VSPackage-spezifischen Objekten.

- [Projektmodellierung](../../extensibility/internals/project-modeling.md)

 Erläutert die Standardprojektobjekte, die zum Erstellen der Automatisierung für den neuen Projekttyp erforderlich sind, und veranschaulicht den Pfad, dem die Projektautomatisierung folgt. In diesem Thema finden Sie auch Auflistungen von Deklarationen und Implementierungen für Klassen.

- [Verfügbar machen Ereignisse](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)

 Enthält Schritt-für-Schritt-Anleitungen zum Erstellen von Ereignissen für Ihr Automatisierungsmodell.

- [Automatisierungsunterstützung für Optionsseiten](../../extensibility/internals/automation-support-for-options-pages.md)

 Beschreibt, wie ein Automatisierungsobjekt zur Unterstützung von Eigenschaften des benutzerdefinierten **Optionsdialogfelds** eines VSPackage im Menü **Werkzeug** zurückgegeben wird, indem das Objekt erweitert wird. `DTE.Properties`

- [Bereitstellen von Automatisierung für Code](../../extensibility/internals/providing-automation-for-code.md)

 Erläutert, dass das Erstellen eines Automatisierungsmodells für Ihren Code nicht erforderlich ist. In diesem Thema wird jedoch ein Link bereitgestellt, der aufschlussreiche Informationen zu Codemodellen bereitstellt.

- [Gewusst wie: Bereitstellen von Automatisierung für Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md)

 Erläutert, dass die Bereitstellung von Automatisierung eine gute Idee ist, wenn Sie Automatisierungsobjekte in einem Fenster verfügbar machen möchten und die Umgebung noch kein vorgefertigtes Automatisierungsobjekt bereitstellt. Erläutert die Automatisierung für Toolfenster und Dokumentfenster.

- [Verwenden des Automatisierungsmodells](../../extensibility/internals/using-the-automation-model.md)

 Enthält zwei Codebeispiele, die zeigen, wie ein Automatisierungsbenutzer die anfänglichen Projektautomatisierungsobjekte abruft.

- [Automatisierung für Konfiguration und SelectedItem-Objekte](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)

 Enthält Informationen zur Automatisierung von Configuration- und SelectedItems-Objekten.

## <a name="reference"></a>Referenz
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>Stellt ein Codebeispiel bereit, das zeigt, wie ein VSPackage am DTE-Automatisierungsobjektmodell beteiligt ist. Listet Parameter, Rückgabewerte und ausgewählte Bemerkungen auf.
