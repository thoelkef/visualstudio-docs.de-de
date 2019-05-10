---
title: Source Control Plug-in-Architektur | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, architecture
ms.assetid: 35351d4c-9414-409b-98fc-f2023e2426b7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ff9c73ebbe976df7c3d25304280e743cad0423c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62908506"
---
# <a name="source-control-plug-in-architecture"></a>Architektur von Quellcodeverwaltungs-Plug-Ins
Sie können die Unterstützung des Datenquellen-Steuerelement zum Hinzufügen der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung (IDE) von Implementierung und Anfügen eines Quellcodeverwaltungs-Plug-in. Die IDE eine Verbindung mit das Quellcodeverwaltungs-Plug-in über die klar definierte Quelle-Plug-in-API. Die IDE stellt Funktionen für die Version von Quellcode-Verwaltungssystem durch Bereitstellen einer Benutzeroberfläche (UI), die der Symbolleisten und Befehle im Menü besteht. Das Quellcodeverwaltungs-Plug-in implementiert die Quellcodeverwaltungsfunktionen.

## <a name="source-control-plug-in-resources"></a>Source Control-Plug-in-Ressourcen
 Die Source-Control-Plug-in enthält Ressourcen, die zum Erstellen und Verbinden der Anwendung versionsverwaltung mit den [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Die Source-Control-Plug-in enthält die API-Spezifikation, die durch ein Quellcodeverwaltungs-Plug-in implementiert werden muss, damit es in integriert werden kann die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Sie enthält auch einen Codebeispiel (geschrieben in C++), eine Skelett Source Control-Plug-in Demonstration-Implementierung von grundlegende Funktionen, die mit der Source-Plug-in-API kompatibel implementiert.

 Die Source-Control-Plug-in-API-Spezifikation können Sie einem beliebigen Quellcodeverwaltungssystem Ihrer Wahl nutzen, bei der Erstellung eines Quellcodeverwaltungs-DLL mit dem erforderlichen Satz von Funktionen, die in Übereinstimmung mit der Source-Plug-in-API implementiert.

## <a name="components"></a>Komponenten
 Das Quellcodeverwaltungspaket Adapter in der Abbildung ist die Komponente der IDE, die die Anforderung des Benutzers für einen Quellcodeverwaltungsvorgang in einem Funktionsaufruf, der durch das Quellcodeverwaltungs-Plug-in unterstützt übersetzt. Um dies zu ermöglichen benötigen die IDE und das Quellcodeverwaltungs-Plug-in eine effektive Dialogfeld, die Informationen hin und her zwischen die IDE und das plug-in übergeben. Für diesen Dialog erfolgen soll müssen beide dieselbe Sprache sprechen. Die Source-Plug-in-API beschrieben, die in dieser Dokumentation wird das gemeinsame Vokabular für diesen Austausch.

 ![Source-Architekturdiagramm](../../extensibility/internals/media/vs_sccsdk_plug_in_arch.gif "Vs_sccsdk_plug_in_arch") -Architekturdiagramm mit Interaktion zwischen VS und Datenquellen-Steuerelement-Plug-in

 Siehe das Architekturdiagramm der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Shell, mit der Bezeichnung als Visual Studio-Shell im Diagramm hostet, funktionierende Projekte und Komponenten, wie die Editoren und den Projektmappen-Explorer des Benutzers. Der Quellcode-Verwaltungspaket Adapter behandelt die Interaktion zwischen der IDE und das Quellcodeverwaltungs-Plug-in. Das Quellcodeverwaltungspaket-Adapter stellt eine eigene Benutzeroberfläche der quellcodeverwaltung bereit. Es ist die obersten Ebene Benutzeroberfläche, die der Benutzer interagiert, um zu initiieren, und legen Sie den Projektumfang einen Quellcodeverwaltungsvorgang.

 Das Quellcodeverwaltungs-Plug-in haben eine eigene Benutzeroberfläche, die aus zwei Teilen bestehen kann, wie in der Abbildung dargestellt. Das Kontrollkästchen "Hersteller UI" darstellt, benutzerdefinierte Elemente der Benutzeroberfläche, die Sie als Quelle Steuerelement-Plug-in Ersteller, bereitstellen. Diese werden direkt durch das Quellcodeverwaltungs-Plug-in angezeigt, wenn der Benutzer eine erweiterte Quellcodeverwaltungsvorgang aufruft. Das Kontrollkästchen "Hilfsprogramm-UI" ist eine Reihe von Datenquellen-Steuerelement-Plug-in Funktionen der Benutzeroberfläche, die indirekt über die IDE aufgerufen werden. Das Quellcodeverwaltungs-Plug-In übergibt Fehlermeldungen im Zusammenhang mit der Benutzeroberfläche der IDE mit speziellen Rückruffunktionen, die von der IDE bereitgestellt. Der Hilfsprogramm-UI ermöglicht eine nahtlosere Integration mit der IDE (häufig durch die Verwendung von einem **erweitert** Schaltfläche) und bietet somit eine einheitliche Benutzeroberfläche.

 Ein Quellcodeverwaltungs-Plug-in kann keine Änderungen vornehmen, um die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] shell und daher entweder das Quellcodeverwaltungspaket-Adapter oder die Quelle steuern Benutzeroberfläche, die von der IDE bereitgestellt. Sie müssen, nutzen die Flexibilität, die durch die Implementierung von den verschiedenen Source Control-Plug-in-API-Funktionen, die auf eine integrierte Umgebung für den Endbenutzer beitragen. Im Referenzabschnitt "der Source-Control-Plug-in-API-Dokumentation enthält Informationen für einige erweiterte Steuerelement-Plug-in-Funktionen. Um diese Features nutzen möchten, muss das Quellcodeverwaltungs-Plug-in Dank der erweiterten Funktionen der IDE deklarieren, während der Initialisierung, und es muss bestimmte erweiterte Funktionen für die einzelnen Funktionen implementieren.

## <a name="see-also"></a>Siehe auch
- [Quellcodeverwaltungs-Plug-Ins](../../extensibility/source-control-plug-ins.md)
- [Glossar](../../extensibility/source-control-plug-in-glossary.md)
- [Erstellen eines Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/creating-a-source-control-plug-in.md)