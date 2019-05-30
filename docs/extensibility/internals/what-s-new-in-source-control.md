---
title: Neuigkeiten in der Quellcodeverwaltung in Visual Studio 2015 SDK | Microsoft-Dokumentation
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e12776c21d345d60992eeff4963498bcd7d56678
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323253"
---
# <a name="whats-new-in-source-control-for-the-visual-studio-2015-sdk"></a>Was ist neu in der Quellcodeverwaltung für das Visual Studio 2015 SDK

In der [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], können Sie eine vollständig integriert Source-Control-Lösung bereitstellen, durch die Implementierung eines Quellcodeverwaltungs-VSPackage. Dieser Abschnitt beschreibt die Funktionen der quellcodeverwaltung VSPackages und bietet eine Übersicht über die Schritte für die Implementierung.

## <a name="the-source-control-vspackage"></a>Der Quellcodeverwaltungs-VSPackage

Visual Studio unterstützt zwei Arten von Quellcode-Kontrollmechanismen. In allen Versionen von Visual Studio, Sie können weiterhin integrieren, eine Source-Control-Plug-in-API-basierte-Plug-in. Sie können auch eine VSPackage für die quellcodeverwaltung, die eine umfassende-Integration bietet erstellen [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Pfad für die Quellcode-Kontrollmechanismen, die ein hohes Maß an Komplexität und Autonomie erfordern geeignet ist.

Eine VSPackage kann nahezu jede Art von Funktionalität zu Visual Studio hinzufügen. Ein Quellcodeverwaltungs-VSPackage bietet eine vollständige Quelle-Steuerelement für Visual Studio, über der Benutzeroberfläche, die dem Benutzer auf die Back-End-Kommunikation mit dem Quellcodeverwaltungssystem angezeigt.

Implementierung eines Quellcodeverwaltungs-VSPackage ist eine Strategie für die "Alles oder nichts" erforderlich. Der Ersteller eines Quellcodeverwaltungs-VSPackage muss sehr viel Aufwand bei der Implementierung einer Reihe von Steuerelement-Schnittstellen und neue Benutzeroberflächenelemente (Dialogfelder, Menüs und Symbolleisten) die gesamte Quelle Listensteuerelement-Funktionalität abgedeckt und Schnittstellen investieren. Alle Pakete erforderlich für die erfolgreiche Integration in Visual Studio.

Die folgenden Schritte bieten einen allgemeinen Überblick darüber, was benötigt wird, um ein Quellcodeverwaltungspaket zu implementieren. Weitere Informationen finden Sie unter [Erstellen eines Quellcodeverwaltungs-VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md).

1. Erstellen Sie eine VSPackage, das einen privaten quellcodeverwaltungsdienst anbietet.

2. Implementieren von Schnittstellen in Quelle Steuerelement-bezogenen Diensten, die von Visual Studio, die angeboten werden (z. B. die <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> Schnittstelle).

3. Registrieren Sie Ihre quellcodeverwaltung VSPackage ein.

4. Implementieren Sie alle Datenquellen-Steuerelement-Benutzeroberfläche, auch werden, Menüelemente, Dialogfelder, Symbolleisten und Kontextmenüs.

5. Alle Datenquellen-Steuerelement-bezogene Ereignisse werden der quellcodeverwaltung VSackage übergeben, wenn er aktiv ist, und vom VSPackage behandelt werden muss.

6. Ihre quellcodeverwaltung VSPackage muss auf Ereignisse, z. B. die implementierende lauschen, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> sowie die Ereignisse des Track-Project-Dokument (TPD)-Schnittstelle (entsprechend der Implementierung durch die <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> Schnittstelle) und erforderliche Maßnahmen.

## <a name="see-also"></a>Siehe auch

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [Übersicht](../../extensibility/internals/source-control-integration-overview.md)
- [Erstellen eines Quellcodeverwaltungs-VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)