---
title: Neuerungen in der Quellcodeverwaltung im Visual Studio 2015 SDK | Microsoft Docs
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f90ae3e1d327b10e99713ad28aa2d5a06c0be34b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703410"
---
# <a name="whats-new-in-source-control-for-the-visual-studio-2015-sdk"></a>Neuerungen in der Quellcodeverwaltung für das Visual Studio 2015 SDK

[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]Im können Sie eine tief integrierte Quellcodeverwaltungslösung bereitstellen, indem Sie ein Quellcodeverwaltungs-VSPackage implementieren. Dieser Abschnitt beschreibt die Funktionen der Quellcodeverwaltung VSPackages und bietet einen Überblick über die Implementierungsschritte.

## <a name="the-source-control-vspackage"></a>Das Quellcodeverwaltung VSPackage

Visual Studio unterstützt zwei Arten von Quellcodeverwaltungslösungen. In allen Versionen von Visual Studio können Sie weiterhin ein Quellsteuerungs-Plug-In-API-basiertes Plug-In integrieren. Sie können auch ein VSPackage für die Quellcodeverwaltung [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] erstellen, das einen Tiefenintegrationspfad bietet, der für Quellcodeverwaltungslösungen geeignet ist, die ein hohes Maß an Raffinesse und Autonomie erfordern.

Ein VSPackage kann Visual Studio fast jede Art von Funktionalität hinzufügen. Ein Quellcodeverwaltungs-VSPackage bietet eine vollständige Quellcodeverwaltungsfunktion für Visual Studio, von der dem Benutzer vorgestellten Benutzeroberfläche bis zur Back-End-Kommunikation mit dem Quellcodeverwaltungssystem.

Das Implementieren einer Quellcodeverwaltung VSPackage erfordert eine "Alles oder Nichts"-Strategie. Der Ersteller eines Quellcodeverwaltungs-VSPackage muss erhebliche Anstrengungen in die Implementierung einer Reihe von Quellcodeverwaltungsschnittstellen und neuen UI-Elementen (Dialogfelder, Menüs und Symbolleisten) investieren, um die gesamte Quellcodeverwaltungsfunktionalität sowie Schnittstellen abzudecken, die für jedes Paket erforderlich sind, um erfolgreich in Visual Studio integriert zu werden.

Die folgenden Schritte geben einen allgemeinen Überblick darüber, was zum Implementieren eines Quellcodeverwaltungspakets erforderlich ist. Weitere Informationen finden Sie unter [Erstellen eines Quellcodeverwaltungs-VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md).

1. Erstellen Sie ein VSPackage, das einen privaten Quellcodeverwaltungsdienst bietet.

2. Implementieren Sie die Schnittstellen in den Quellcodeverwaltungsdiensten, die von Visual <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> Studio <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> angeboten werden (z. B. die und die Schnittstelle).

3. Registrieren Sie Ihre Quellcodeverwaltung VSPackage.

4. Implementieren Sie alle Quellcodeverwaltungsbenutzeroberflächen, einschließlich Menüelemente, Dialogfelder, Symbolleisten und Kontextmenüs.

5. Alle Quellsteuerungsereignisse werden an Ihre Quellcodeverwaltung VSackage übergeben, wenn sie aktiv ist, und müssen von Ihrem VSPackage behandelt werden.

6. Ihr Quellcodeverwaltungs-VSPackage muss Ereignisse wie <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> die Implementierung der Schnittstelle sowie TPD-Ereignisse (track <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> Project Document) (wie von der Schnittstelle implementiert) abhören und die erforderlichen Maßnahmen ergreifen.

## <a name="see-also"></a>Weitere Informationen

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [Übersicht](../../extensibility/internals/source-control-integration-overview.md)
- [Erstellen eines Quellcodeverwaltungs-VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)
