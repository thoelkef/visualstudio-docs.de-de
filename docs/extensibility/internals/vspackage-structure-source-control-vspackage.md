---
title: VSPackage-Struktur (Quellcodeverwaltung VSPackage) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b3f09b189e1e4b47187586e66c74315ee32495c8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703812"
---
# <a name="vspackage-structure-source-control-vspackage"></a>VSPackage-Struktur (Quellcodeverwaltungs-VSPackage)

Das Source Control Package SDK enthält Richtlinien zum Erstellen eines VSPackage, mit dem ein Quellcodeverwaltungsimplementierer seine Quellcodeverwaltungsfunktionalität in die Visual Studio-Umgebung integrieren kann. Ein VSPackage ist eine COM-Komponente, die in der Regel bei Bedarf von der integrierten Visual Studio-Entwicklungsumgebung (IDE) basierend auf den Diensten geladen wird, die vom Paket in seinen Registrierungseinträgen angekündigt werden. Jedes VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>muss implementieren. Ein VSPackage nutzt in der Regel Dienste, die von der Visual Studio-IDE angeboten werden, und bietet einige eigene Dienste an.

Ein VSPackage deklariert seine Menüelemente und richtet über die .vsct-Datei einen Standardelementstatus ein. Die Visual Studio-IDE zeigt die Menüelemente in diesem Zustand an, bis das VSPackage geladen wird. Anschließend wird die VsPackage-Implementierung <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> der Methode aufgerufen, um Menüelemente zu aktivieren oder zu deaktivieren.

## <a name="source-control-package-characteristics"></a>Eigenschaften des Quellcodeverwaltungspakets

Ein Quellcodeverwaltungs-VSPackage ist tief in Visual Studio integriert. Die VSPackage-Semantik umfasst:

- Schnittstelle, die als VSPackage (die `IVsPackage` Schnittstelle) implementiert werden soll

- UI Command-Implementierung (.vsct-Datei <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> und Implementierung der Schnittstelle)

- Registrierung des VSPackage bei Visual Studio.

Das Quellcodeverwaltungs-VSPackage muss mit diesen anderen Visual Studio-Entitäten kommunizieren:

- Projekte

- Editoren

- Lösungen

- Windows

- Die laufende Dokumenttabelle

### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Visual Studio-Umgebungsdienste, die möglicherweise verwendet werden

<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>

SVsRegisterScciProvider-Dienst

<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>

### <a name="vsip-interfaces-implemented-and-called"></a>VSIP-Schnittstellen implementiert und aufgerufen

Ein Quellcodeverwaltungspaket ist ein VSPackage und kann daher direkt mit anderen VSPackages interagieren, die bei Visual Studio registriert sind. Um die volle Bandbreite der Quellcodeverwaltungsfunktionalität bereitzustellen, kann ein Quellcodeverwaltungs-VSPackage Schnittstellen von Projekten oder der Shell behandeln.

Jedes Projekt in Visual <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> Studio muss implementiert werden, um als Projekt innerhalb der Visual Studio-IDE erkannt zu werden. Diese Schnittstelle ist jedoch nicht speziell genug für die Quellcodeverwaltung. Projekte, von denen erwartet wird, dass sie unter Quellcodeverwaltung stehen, implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>. Diese Schnittstelle wird vom Quellcodeverwaltungssteuerelement VSPackage verwendet, um ein Projekt nach seinem Inhalt abzufragen und es Glyphen und Bindungsinformationen bereitzustellen (die Informationen, die zum Herstellen einer Verbindung zwischen dem Serverspeicherort und dem Datenträgerspeicherort eines Projekts erforderlich sind, das unter Quellcodeverwaltung steht).

Die Quellcodeverwaltung VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>implementiert , was es Projekten wiederum ermöglicht, sich selbst für die Quellcodeverwaltung zu registrieren und ihre Status-Glyphen abzurufen.

Eine vollständige Liste der Schnittstellen, die ein Quellcodeverwaltungs-VSPackage berücksichtigen muss, finden Sie unter [Verwandte Dienste und Schnittstellen](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md).

## <a name="see-also"></a>Weitere Informationen

- [Entwurfselemente](../../extensibility/internals/source-control-vspackage-design-elements.md)
- [Verwandte Dienste und Schnittstellen](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)
