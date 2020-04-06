---
title: Überblick über die Quellcodeverwaltungsintegration | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], about source control
ms.assetid: 3a46e4eb-e677-49c3-8647-d927d035a19a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d80363286f5f0cac9a5ceb2e8ac9d20345df9e6f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705120"
---
# <a name="source-control-integration-overview"></a>Übersicht über die Integration der Quellcodeverwaltung
In diesem Abschnitt werden die beiden Möglichkeiten der Integration in die Visual Studio-Quellcodeverwaltung verglichen. ein Quellcodeverwaltungs-Plug-In und ein VSPackage, das eine Quellcodeverwaltungslösung bereitstellt und die neuen Quellcodeverwaltungsfunktionen hervorhebt. Visual Studio ermöglicht das manuelle Umschalten zwischen Quellcodeverwaltung VSPackages und Quellcodeverwaltungs-Plug-Ins sowie automatisches lösungsbasiertes Switching.

## <a name="source-control-integration"></a>Integration der Quellcodeverwaltung
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]unterstützt zwei Arten von Quellcodeverwaltungsintegrationsoptionen. In allen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Versionen von können Sie weiterhin ein Plug-In basierend auf der Quellcodeverwaltungs-Plug-In-API (früher auch als MSSCCI-API bezeichnet) integrieren, die grundlegende Quellcodeverwaltungsfunktionen bei Verwendung der Visual Studio-Quellcodeverwaltungsbenutzeroberfläche (UI) bereitstellt. Ein Quellcodeverwaltungs-VSPackage hingegen bietet einen neuen, tiefen [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Integrationspfad, der für die Quellcodeverwaltungsintegration geeignet ist und ein hohes Maß an Raffinesse und Autonomie in seinem Quellcodeverwaltungsmodell erfordert.

 ![Übersicht über die Quellcodeverwaltung](../../extensibility/internals/media/sourcectnrloverview.gif "SourceCtnrlÜbersicht")

## <a name="source-control-plug-in"></a>Quellcodeverwaltung Plug-in
 Alle Versionen von Visual Studio unterstützen die Quellsteuerungs-Plug-In-API-Spezifikation Version 1.2 als Integrationspfad. Ein Quellcodeverwaltungs-Plug-In-Implementierer schreibt eine DLL, die die Quellcodeverwaltungs-Plug-In-API-Funktionen für die Quellcodeverwaltungsintegration und -registrierung implementiert, wie unter [Erstellen eines Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/creating-a-source-control-plug-in.md)beschrieben. Bei diesem Ansatz verwendet die Integrierte Entwicklungsumgebung (IDE) die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Benutzeroberfläche für Dialogfelder, z. B. Einchecken, Auschecken, Tools/Options-Eigenschaftenseiten, Symbolleisten und Quellcodeverwaltungsglyphen. Die strikte Einhaltung der Quellcodeverwaltungs-Plug-In-API stellt eine einfache Integration in Visual Studio und eine problemlose Erfahrung für den Benutzer sicher. Dies bedeutet, dass das Quellcodeverwaltungs-Plug-In die meisten Funktionen und Rückrufe implementieren muss, die in der API beschrieben sind.

 Gehen Sie folgendzubearid vor, um ein Quellcodeverwaltungs-Plug-In mithilfe der Quellcodeverwaltungs-Plug-In-API zu implementieren:

1. Erstellen Sie eine DLL, die die in [Denksteuerungs-Plug-Ins](../../extensibility/source-control-plug-ins.md)angegebenen Funktionen implementiert.

2. Registrieren Sie die DLL, indem Sie die entsprechenden Registrierungseinträge vornehmen (siehe [Gewusst wie: Installieren eines Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)).

3. Erstellen einer Hilfsbenutzeroberfläche und Anzeige, wenn vom Quellcodeverwaltungsadapterpaket aufgefordert (die Visual Studio-Komponente, die die Quellcodeverwaltungsfunktionalität über Quellcodeverwaltungs-Plug-Ins verarbeitet)

   Als Reaktion auf einen Quellcodeverwaltungsbefehl stellt die Visual Studio-IDE eine Standard-BEnutzeroberfläche für die grundlegenden Vorgänge dar und übergibt die Informationen dann über die in der Quellcodeverwaltungs-Plug-In-API definierten Funktionen an das Quellcodeverwaltungs-Plug-In. Für erweiterte Optionen kann das Quellcodeverwaltungs-Plug-In aufgerufen werden, um eine eigene Benutzeroberfläche zu präsentieren, z. B. das Durchsuchen eines Projekts unter Quellcodeverwaltung. Dies bedeutet, dass dem Benutzer möglicherweise zwei möglicherweise unterschiedliche Benutzeroberflächenstile angezeigt werden, wenn er mit der Quellcodeverwaltung zu tun hat: die benutzeroberfläche, die Visual Studio darstellt, und die Benutzeroberfläche, die das Quellcodeverwaltungs-Plug-In darstellt. Dies ist am deutlichsten bei erweiterten Quellcodeverwaltungsvorgängen.

### <a name="drawbacks-to-implementing-a-source-control-plug-in"></a>Nachteile beim Implementieren eines Quellcodeverwaltungs-Plug-Ins

- Für erweiterte Funktionen kann der Benutzer zwei verschiedene Arten von Schnittstellen sehen, was zu möglichen Verwirrungen führt.

- Das Quellcodeverwaltungs-Plug-In ist auf das Quellcodeverwaltungsmodell beschränkt, das von der Quellcodeverwaltungs-Plug-In-API impliziert wird.

- Die Quellcodeverwaltungs-Plug-In-API ist für einige Quellcodeverwaltungsszenarien möglicherweise zu restriktiv.

### <a name="advantages-to-implementing-a-source-control-plug-in"></a>Vorteile beim Implementieren eines Quellcodeverwaltungs-Plug-Ins

- Visual Studio stellt die gesamte Benutzeroberfläche für alle grundlegenden Quellcodeverwaltungsvorgänge bereit, sodass das Quellcodeverwaltungs-Plug-In keine potenziell komplexe Benutzeroberfläche implementieren muss.

- Aufgrund der strengen API kann das Quellcodeverwaltungs-Plug-In problemlos mit externen Quellcodeverwaltungsprogrammen interagieren, um umfangreichere Funktionen bereitzustellen. Visual Studio ist es egal, wie die Quellcodeverwaltungsfunktionalität erreicht wird, sondern nur, dass sie gemäß der Quellcodeverwaltungs-Plug-In-API durchgeführt wird.

- Es ist einfacher, ein Quellcodeverwaltungs-Plug-In als ein Quellcodeverwaltungs-VSPackage zu implementieren.

## <a name="source-control-vspackage"></a>Quellcodeverwaltung VSPackage
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]ermöglicht eine umfassende Integration in Visual Studio mit vollständiger Kontrolle der Quellcodeverwaltungsfunktionalität und vollständigem Austausch der von Visual Studio bereitgestellten Benutzeroberfläche für die Quellcodeverwaltung. Ein Quellcodeverwaltungs-VSPackage ist bei Visual Studio registriert und bietet Quellcodeverwaltungsfunktionen. Obwohl mehrere Quellcodeverwaltungs-VSPackages bei Visual Studio registriert werden können, kann nur eines von ihnen gleichzeitig aktiv sein. Ein Quellcodeverwaltungs-VSPackage hat die volle Kontrolle über die Quellcodeverwaltungsfunktionalität und das Erscheinungsbild in Visual Studio, während es aktiv ist. Alle anderen Quellcodeverwaltungs-VSPackages, die im System registriert werden können, sind inaktiv und zeigen überhaupt keine Benutzeroberfläche an.

 Das Implementieren einer Quellcodeverwaltung VSPackage erfordert eine "Alles oder Nichts"-Strategie. Der Ersteller eines Quellcodeverwaltungs-VSPackage muss erhebliche Anstrengungen in die Implementierung einer Reihe von Quellcodeverwaltungsschnittstellen und neuen UI-Elementen (Dialogfelder, Menüs und Symbolleisten) investieren, um die gesamte Quellcodeverwaltungsfunktionalität abzudecken. Weitere Informationen finden Sie unter [Erstellen eines Quellcodeverwaltungs-VSPackage.](../../extensibility/internals/creating-a-source-control-vspackage.md)

### <a name="drawbacks-to-implementing-a-source-control-vspackage"></a>Nachteile beim Implementieren eines Quellcodeverwaltungs-VSPackage

- Das VSPackage muss eine Reihe komplexer Schnittstellen implementieren, um erfolgreich in Visual Studio integriert zu werden.

- Das VSPackage muss die gesamte für die Quellcodeverwaltung erforderliche Benutzeroberfläche bereitstellen. Visual Studio bietet in diesem Bereich keine Unterstützung.

- Ein Quellcodeverwaltungs-VSPackage ist eng mit Visual Studio verbunden und kann nicht mit eigenständigen Programmen betrieben werden, sodass die Funktionalität nicht so einfach mit einer externen Version des Quellcodeverwaltungsprogramms geteilt werden kann.

### <a name="advantages-to-implementing-a-source-control-vspackage"></a>Vorteile der Implementierung eines Quellcodeverwaltungs-VSPackage

- Da das VSPackage die volle Kontrolle über die Quellcodeverwaltungsbenutzeroberfläche und -funktionalität hat, wird dem Benutzer eine nahtlose Schnittstelle für die Quellcodeverwaltung angezeigt.

- Das VSPackage ist nicht auf ein bestimmtes Quellcodeverwaltungsmodell beschränkt.

## <a name="see-also"></a>Weitere Informationen
- [Quellsteuerung](../../extensibility/internals/source-control.md)
- [Erstellen eines Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [Erstellen eines Quellcodeverwaltungs-VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)
- [Neuigkeiten in der Quellcodeverwaltung](../../extensibility/internals/what-s-new-in-source-control.md)
