---
title: VSPackage-Struktur (Quellcodeverwaltungs-VSPackage) | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03b9d4fb6a92694df55d6732ac80d75645209a87
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62857063"
---
# <a name="vspackage-structure-source-control-vspackage"></a>VSPackage-Struktur (Quellcodeverwaltungs-VSPackage)

Die Source-Steuerelement-Paket-SDK bietet Richtlinien zum Erstellen von einer VSPackages, die eine Quelle Steuerelement Implementierer seine Quellcodeverwaltungsfunktionen in Visual Studio-Umgebung integrieren können. Ein VSPackage ist eine COM-Komponente, die in der Regel geladen wird bei Bedarf von der Visual Studio integrierten Entwicklungsumgebung (IDE) basierend auf den Diensten, die von das Paket in seine Registrierungseinträge vorgenommen angekündigt werden. Jedes VSPackage implementieren muss <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>. Eine VSPackage in der Regel nutzt Dienste, die von Visual Studio-IDE und einige eigene-Dienste anbietet.

Eine VSPackage deklariert seine Menüelemente und richtet einen Standardzustand des Elements über der VSCT-Datei ein. Visual Studio-IDE zeigt die Menüelemente in diesem Zustand, bis das VSPackage geladen wird. Anschließend kann die VSPackage Implementierung von der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> aufgerufen, um aktivieren oder Deaktivieren von Menüelementen.

## <a name="source-control-package-characteristics"></a>Source-Paket Eigenschaften

Ein Quellcodeverwaltungs-VSPackage ist umfassend in Visual Studio integriert. Die VSPackage-Semantik gehören:

- Schnittstelle, die aufgrund ihrer Zugehörigkeit zu einem VSPackage implementiert werden (die `IVsPackage` Schnittstelle)

- Benutzeroberfläche-Implementierung (VSCT-Datei und die Implementierung der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle)

- Die Registrierung des VSPackage in Visual Studio.

Das Datenquellen-Steuerelement muss VSPackage mit diesen anderen Visual Studio-Entitäten kommunizieren:

- Projekte

- Editoren

- Projektmappen

- Windows

- Die aktive Dokumenttabelle

### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Visual Studio-Umgebung-Dienste, die genutzt werden kann

<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>

SVsRegisterScciProvider Service

<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>

### <a name="vsip-interfaces-implemented-and-called"></a>VSIP-Schnittstellen implementiert und wird aufgerufen

Ein Quellcodeverwaltungspaket ist ein VSPackage, und es kann daher interagieren direkt mit anderen VSPackages, die mit Visual Studio registriert sind. Um die gesamte Bandbreite der quellcodeverwaltung zu gewährleisten, kann ein Datenquellen-Steuerelement Projekte oder die Shell bereitgestellten Schnittstellen für VSPackage behandeln.

Jedes Projekt in Visual Studio muss implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> , als ein Projekt in Visual Studio-IDE erkannt werden soll. Diese Schnittstelle ist jedoch nicht spezialisiert genug für die quellcodeverwaltung. Projekte, die als quellcodeverwaltung werden steuern implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>. Diese Schnittstelle wird durch das Quellcodeverwaltungs-VSPackage verwendet, zum Abfragen von ein Projekt für deren Inhalte und Symbole und Bindungsinformationen (die erforderlichen Informationen zum Herstellen einer Verbindung zwischen den Serverstandort und den Speicherort eines Projekts, die unter Bereitstellen Datenquellen-Steuerelement).

Das Datenquellen-Steuerelement, das VSPackage implementiert <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, wodurch wiederum ermöglicht Projekten, registrieren sich für die quellcodeverwaltung und deren Status Symbole abrufen.

Eine vollständige Liste der Schnittstellen, die ein Quellcodeverwaltungs-VSPackage berücksichtigen müssen, finden Sie unter [Verwandte Dienste und Schnittstellen](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md).

## <a name="see-also"></a>Siehe auch

- [Entwurfselemente](../../extensibility/internals/source-control-vspackage-design-elements.md)
- [Verwandte Dienste und Schnittstellen](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)