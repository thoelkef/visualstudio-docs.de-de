---
title: Quellcodeverwaltung Plug-In-Architektur | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, architecture
ms.assetid: 35351d4c-9414-409b-98fc-f2023e2426b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f549ad2c4ee456860a08fbf20ccda813934a8582
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705110"
---
# <a name="source-control-plug-in-architecture"></a>Architektur von Quellcodeverwaltungs-Plug-Ins
Sie können der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung (IDE) Quellcodeverwaltungsunterstützung hinzufügen, indem Sie ein Quellcodeverwaltungs-Plug-In implementieren und anfügen. Die IDE stellt über die klar definierte Quellcodeverwaltungs-Plug-In-API eine Verbindung zum Quellcodeverwaltungs-Plug-In her. Die IDE macht die Versionssteuerungsfunktionen des Quellcodeverwaltungssystems verfügbar, indem eine Benutzeroberfläche (UI) bereitgestellt wird, die aus Symbolleisten und Menübefehlen besteht. Das Quellcodeverwaltungs-Plug-In implementiert die Quellcodeverwaltungsfunktionalität.

## <a name="source-control-plug-in-resources"></a>Quellcodeverwaltung Plug-In-Ressourcen
 Das Quellcodeverwaltungs-Plug-In stellt Ressourcen zum Erstellen und [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Verbinden ihrer Versionsanwendung mit der IDE bereit. Das Quellcodeverwaltungs-Plug-In enthält die API-Spezifikation, die von einem Quellcodeverwaltungs-Plug-In implementiert werden muss, damit es in die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE integriert werden kann. Es enthält auch ein Codebeispiel (in C++geschrieben), das ein Skelett-Quellcodeverwaltungs-Plug-In implementiert, das die Implementierung wesentlicher Funktionen demonstriert, die mit der Quellcodeverwaltungs-Plug-In-API kompatibel sind.

 Mit der Source Control Plug-in-API-Spezifikation können Sie jedes Quellcodeverwaltungssystem Ihrer Wahl nutzen, wenn Sie eine Quellcodeverwaltungs-DLL mit den erforderlichen Funktionen erstellen, die in Übereinstimmung mit der Quellcodeverwaltungs-Plug-In-API implementiert sind.

## <a name="components"></a>Komponenten
 Das Quellcodeverwaltungsadapterpaket im Diagramm ist die Komponente der IDE, die die Anforderung des Benutzers für einen Quellcodeverwaltungsvorgang in einen Vom Quellcodeverwaltungs-Plug-In unterstützten Funktionsaufruf übersetzt. Dazu müssen die IDE und das Quellcodeverwaltungs-Plug-In über ein effektives Dialogfeld verfügen, das Informationen zwischen der IDE und dem Plug-In hin und her übergibt. Damit dieser Dialog stattfindet, müssen beide dieselbe Sprache sprechen. Die in dieser Dokumentation beschriebene Quellcodeverwaltungs-Plug-In-API ist das gängige Vokabular für diesen Austausch.

 ![Quellcodesteuerungs-Architekturdiagramm](../../extensibility/internals/media/vs_sccsdk_plug_in_arch.gif "vs_sccsdk_plug_in_arch") Architekturdiagramm mit Interaktion zwischen VS und Quellcodeverwaltungs-Plug-In

 Wie im Architekturdiagramm gezeigt, hostet die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Shell, die im Diagramm als VS-Shell gekennzeichnet ist, die Arbeitsprojekte des Benutzers und die zugehörigen Komponenten, z. B. die Editoren und den Projektmappen-Explorer. Das Quellcodeverwaltungsadapterpaket verarbeitet die Interaktion zwischen der IDE und dem Quellcodeverwaltungs-Plug-In. Das Quellcodeverwaltungsadapterpaket stellt eine eigene Quellcodeverwaltungsbenutzeroberfläche bereit. Es ist die Benutzeroberfläche der obersten Ebene, mit der der Benutzer interagiert, um den Umfang eines Quellcodeverwaltungsvorgangs zu initiieren und zu definieren.

 Das Quellcodeverwaltungs-Plug-In kann über eine eigene Benutzeroberfläche verfügen, die aus zwei Teilen bestehen kann, wie in der Abbildung dargestellt. Das Feld mit der Bezeichnung "Vendor UI" stellt benutzerdefinierte Benutzeroberflächenelemente dar, die Sie als Source control Plug-In-Ersteller bereitstellen. Diese werden direkt vom Quellcodeverwaltungs-Plug-In angezeigt, wenn der Benutzer einen erweiterten Quellcodeverwaltungsvorgang aufruft. Das Feld mit der Bezeichnung "Hilfebenutzeroberfläche" ist ein Satz von Quellcodeverwaltungs-Plug-In-UI-Features, die indirekt über die IDE aufgerufen werden. Das Quellcodeverwaltungs-Plug-In übergibt UI-bezogene Nachrichten an die IDE über spezielle Rückruffunktionen, die von der IDE bereitgestellt werden. Die Hilfs-Benutzeroberfläche ermöglicht eine nahtlosere Integration mit der **Advanced** IDE (häufig durch die Verwendung einer Advanced-Schaltfläche) und bietet somit eine einheitlichere Endbenutzererfahrung.

 Ein Quellcodeverwaltungs-Plug-In kann [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] keine Änderungen an der Shell und damit am Quellcodeverwaltungsadapterpaket oder an der von der IDE bereitgestellten Quellcodeverwaltungsbenutzeroberfläche vornehmen. Sie muss die Flexibilität, die durch die Implementierung der verschiedenen Source Control Plug-in-API-Funktionen geboten wird, die zu einer integrierten Erfahrung für den Endbenutzer beitragen, maximal nutzen. Der Referenzabschnitt der Source Control Plug-In-API-Dokumentation enthält Informationen für einige erweiterte Quellcodeverwaltungs-Plug-In-Funktionen. Um diese Features zu nutzen, muss das Quellcodeverwaltungs-Plug-In seine erweiterten Funktionen während der Initialisierung für die IDE deklarieren und für jede Funktion bestimmte erweiterte Funktionen implementieren.

## <a name="see-also"></a>Weitere Informationen
- [Quellcodeverwaltungs-Plug-Ins](../../extensibility/source-control-plug-ins.md)
- [Glossar](../../extensibility/source-control-plug-in-glossary.md)
- [Erstellen eines Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/creating-a-source-control-plug-in.md)
