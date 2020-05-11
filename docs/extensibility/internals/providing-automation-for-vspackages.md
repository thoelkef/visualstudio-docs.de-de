---
title: Automatisierung für VSPackages | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, automation [Visual Studio SDK]
- automation [Visual Studio SDK], VSPackages
ms.assetid: 104c4c55-78b8-42f4-b6b0-9a334101aaea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6364f9cbaf3409e076eeb77365e5d793c7be96cb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705948"
---
# <a name="providing-automation-for-vspackages"></a>Bereitstellen von Automatisierung für VSPackages
Es gibt zwei Hauptmöglichkeiten, um die Automatisierung Ihrer VSPackages bereitzustellen: durch die Implementierung von VSPackage-spezifischen Objekten und durch die Implementierung von Standardautomatisierungsobjekten. Im Allgemeinen werden diese zusammen verwendet, um das Automatisierungsmodell der Umgebung zu erweitern.

## <a name="vspackage-specific-objects"></a>VSPackage-spezifische Objekte
 An bestimmten Stellen innerhalb des Automatisierungsmodells müssen Sie Automatisierungsobjekte bereitstellen, die für Ihr VSPackage eindeutig sind. Beispielsweise erfordern neue Projekte unterschiedliche Objekte, die nur Ihr VSPackage bereitstellt. Die Namen dieser Objekte werden in der Registrierung eingegeben `DTE` und durch Aufrufe des Umgebungsobjekts abgerufen.

 VSPackage-spezifische Objekte können auch abgerufen werden, wenn ein Automatisierungsverbraucher das Objekt verwendet, das über die Object-Eigenschaft eines Standardobjekts bereitgestellt wird. Das Standardobjekt `Window` verfügt beispielsweise `Object` über eine Eigenschaft, die allgemein als Eigenschaft bezeichnet wird. `Windows.Object` Wenn Verbraucher `Window.Object` die in einem in Ihrem VSPackage implementierten Fenster aufrufen, geben Sie ein bestimmtes Automatisierungsobjekt Ihres eigenen Designs zurück.

#### <a name="projects"></a>Projekte
 VSPackages kann das Automatisierungsmodell für neue Projekttypen um eigene VSPackage-spezifische Objekte erweitern. Der Hauptzweck der Bereitstellung neuer Automatisierungsobjekte für Ihr VSPackage <xref:Microsoft.VisualStudio.VCProjectEngine.VCProject> besteht <xref:VSLangProj80.VSProject2> darin, Ihre eindeutigen Projektobjekte von einem oder einem Objekt zu unterscheiden. Diese Differenzierung ist praktisch, wenn Sie eine Möglichkeit bieten möchten, Ihren Projekttyp neben anderen Projekttypen herauszuarbeiten oder zu iterieren, falls sie in einer Projektmappe nebeneinander angezeigt werden. Weitere Informationen finden Sie unter [Verlarven von Projektobjekten](../../extensibility/internals/exposing-project-objects.md).

#### <a name="events"></a>Ereignisse
 Die Eventarchitektur der Umgebung bietet Ihnen einen weiteren Ort, an den Sie Ihre eigenen VSPackage-spezifischen Objekte anhängen können. Wenn Sie beispielsweise eigene eindeutige Ereignisobjekte erstellen, können Sie das Ereignismodell der Umgebung für Projekte erweitern. Sie können eigene Ereignisse bereitstellen, wenn ein neues Element zu Ihrem eigenen Projekttyp hinzugefügt wird. Weitere Informationen finden Sie unter [Aussetzen von Ereignissen](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md).

#### <a name="window-objects"></a>Fensterobjekte
 Windows kann ein VSPackage-spezifisches Automatisierungsobjekt beim Aufruf an die Umgebung zurückgeben. Sie implementieren ein Objekt, <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject> <xref:EnvDTE.IExtensibleObject> das `IDispatch` von abgeleitet ist oder Eigenschaften zurückgibt, wodurch das Fensterobjekt erweitert wird, in dem es erstellt wird. Sie können diesen Ansatz beispielsweise verwenden, um die Automatisierung für ein Steuerelement bereitzustellen, das in einem Fensterrahmen ausgeführt wird. Die Semantik dieses Objekts und aller anderen Objekte, die es erweitern könnte, gehören zu ihrem Entwurf. Weitere Informationen finden Sie unter [Gewusst wie: Bereitstellen von Automatisierung für Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md).

#### <a name="options-pages-on-the-tools-menu"></a>Optionsseiten im Menü Extras
 Sie können Seiten erstellen, um das Automatisierungsmodell Extras, Optionen zu erweitern, indem Sie Seiten implementieren und der Registrierung Informationen hinzufügen, um eigene Optionen zu erstellen. Ihre Seiten können dann wie alle anderen Optionsseiten über das Umgebungsobjektmodell aufgerufen werden. Wenn der Entwurf des Features, das Sie der Umgebung über VSPackages hinzufügen, Optionsseiten erfordert, sollten Sie auch die Automatisierungsunterstützung hinzufügen. Weitere Informationen finden Sie unter [Automatisierungsunterstützung für Optionsseiten](../../extensibility/internals/automation-support-for-options-pages.md).

## <a name="standard-automation-objects"></a>Standardautomatisierungsobjekte
 Um die Automatisierung für Projekte zu erweitern, implementieren `IDispatch`Sie auch Standardautomatisierungsobjekte (abgeleitet von ), die neben den anderen Projektobjekten stehen und Standardmethoden und -eigenschaften implementieren. Beispiele für Standardobjekte sind die Projektobjekte, die in `Projects` `Project`die `ProjectItem`Projektmappenhierarchie eingefügt werden, z. B. , , und `ProjectItems`. Jeder neue Projekttyp sollte diese Objekte (und möglicherweise andere Objekte je nach Semantik Ihres Projekts) implementieren.

 In gewissem Sinne bieten diese Objekte den gegenteiligen Vorteil der VSPackage-spezifischen Projektobjekte. Die Standardautomatisierungsobjekte ermöglichen die allgemeine Verwendung Ihres Projekts wie jedes andere Projekt, das dieselben Objekte unterstützt. Daher kann ein Add-In, `Project` das `ProjectItem` gegen Allgemein geschrieben wird und Objekte für Projekte jeder Art funktionieren. Weitere Informationen finden Sie unter [Projektmodellierung](../../extensibility/internals/project-modeling.md).
