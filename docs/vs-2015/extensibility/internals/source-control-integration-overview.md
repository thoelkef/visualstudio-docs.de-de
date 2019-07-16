---
title: Übersicht über die Integration Source | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], about source control
ms.assetid: 3a46e4eb-e677-49c3-8647-d927d035a19a
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4e2761958cd60721ccf05a14ec54d3e365572ea1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68148372"
---
# <a name="source-control-integration-overview"></a>Übersicht über die Integration der Quellcodeverwaltung
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dieser Abschnitt vergleicht zwei Möglichkeiten, die in Visual Studio-quellcodeverwaltung integrieren. ein Quellcodeverwaltungs-Plug-in und ein VSPackage, das eine Source-Control-Lösung bietet und die neuen Quellcodeverwaltungsfeatures hervorgehoben. Visual Studio können für manuelle Wechseln zwischen quellcodeverwaltung VSPackages und Quellcodeverwaltungs-Plug-ins als auch automatische informationsreiche lösungsbasierte wechseln.  
  
## <a name="source-control-integration"></a>Integration der quellcodeverwaltung  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] unterstützt zwei Arten der Integration von Quellcodeverwaltungsoptionen. In allen Versionen von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], Sie können immer noch ein plug-in basierend auf der Source-Plug-in-API (zuvor auch bezeichnet als MSSCCI-API), die grundlegende Quellcodeverwaltungsfunktionen bereitstellt, bei der Verwendung von Visual Studio Source Control Benutzer-Schnittstelle (integrieren (UI). Ein Quellcodeverwaltungs-VSPackage, auf der anderen Seite bietet eine neue, umfassende-Integration [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] Pfad für die Integration der quellcodeverwaltung, die ein hohes Maß an Komplexität und Autonomie in seine quellcodeverwaltungmodell Anforderungen geeignet ist.  
  
 ![Übersicht über das Steuerelement Source](../../extensibility/internals/media/sourcectnrloverview.gif "SourceCtnrlOverview")  
  
## <a name="source-control-plug-in"></a>Quellcodeverwaltung-Plug-in  
 Alle Versionen von Visual Studio unterstützen die Source-Plug-in-API-Sprachspezifikation Version 1.2 als Integration Pfad. Eine Quelle Steuerelement-Plug-in Implementierer schreibt eine DLL, die Source-Control-Plug-in-API-Funktionen für die Integration der quellcodeverwaltung und Registrierung implementiert, wie in beschrieben [ein Datenquellen-Steuerelement-Plug-in erstellen](../../extensibility/internals/creating-a-source-control-plug-in.md). Bei diesem Ansatz die integrierte Entwicklungsumgebung (IDE) verwendet die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Benutzeroberfläche für Dialogfelder, z. B. Einchecken, Auschecken, Extras/Optionen Eigenschaftenseiten, Symbolleisten und Quellcodeverwaltungssymbole. Strenge Einhaltung der Source-Plug-in-API ist eine einfache Integration in Visual Studio und eine problemlose-Erfahrung für den Benutzer sichergestellt. Dies bedeutet, dass das Quellcodeverwaltungs-Plug-in implementieren muss, die meisten Funktionen und Rückrufe, die in der API beschrieben.  
  
 Gehen Sie folgendermaßen vor, um ein Quellcodeverwaltungs-Plug-in mit der Source-Plug-in-API zu implementieren:  
  
1. Erstellen Sie eine DLL, die die angegebenen Funktionen implementiert [Quellcodeverwaltung-Plug-ins](../../extensibility/source-control-plug-ins.md).  
  
2. Die DLL registrieren, indem Sie die entsprechenden Registrierungseinträge vornehmen (beschrieben [Vorgehensweise: Installieren eines Quellcodeverwaltungs-Plug-in](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)).  
  
3. Erstellen Sie eine Hilfsprogramm, Benutzeroberfläche und anzeigen, wenn Sie aufgefordert werden, durch den Adapter Quellcodeverwaltungspaket (der Visual Studio-Komponente, verarbeitet der Quellcodeverwaltungsfunktionen über den Quellcodeverwaltungs-Plug-ins)  
  
   Als Reaktion auf ein Steuerelement-Befehl "Quelle" Visual Studio-IDE bietet eine standardmäßige Benutzeroberfläche für die grundlegenden Vorgänge und übergibt dann die Informationen an das Quellcodeverwaltungs-Plug-in über die Funktionen, die in der Quelle-Plug-in-API definiert. Um erweiterte Optionen kann das Quellcodeverwaltungs-Plug-in auf aufgerufen werden, um eine eigene Benutzeroberfläche, anzuzeigen, z. B. für ein Projekt der quellcodeverwaltung unterliegende durchsuchen. Dies bedeutet, dass dem Benutzer zwei möglicherweise verschiedene Arten der Benutzeroberfläche kann beim Umgang mit den Datenquellen-Steuerelement angezeigt werden: die Benutzeroberfläche, die Visual Studio stellt und die Benutzeroberfläche, in dem das Quellcodeverwaltungs-Plug-in dargestellt. Dies ist am deutlichsten für erweiterte Quellcodeverwaltungsvorgänge.  
  
### <a name="drawbacks-to-implementing-a-source-control-plug-in"></a>Nachteile der Implementierung eines Quellcodeverwaltungs-Plug-in  
  
- Erweiterte Funktionen kann der Benutzer zwei verschiedene Arten der Schnittstellen, finden Sie unter was zu Verwechslungen.  
  
- Das Quellcodeverwaltungs-Plug-in ist auf das quellcodeverwaltungmodell impliziert durch die Source-Plug-in-API beschränkt.  
  
- Die Source-Plug-in-API kann für einige Szenarien für Steuerelement zu restriktiv sein.  
  
### <a name="advantages-to-implementing-a-source-control-plug-in"></a>Vorteile der Implementierung eines Quellcodeverwaltungs-Plug-in  
  
- Visual Studio stellt keine Benutzeroberfläche für alle grundlegenden Quellcodeverwaltungsvorgänge, damit das Quellcodeverwaltungs-Plug-in keine potenziell komplexen Benutzeroberfläche zu implementieren.  
  
- Aufgrund der strict-API kann das Quellcodeverwaltungs-Plug-in leicht externen Quelle Steuerelement Benutzerinteraktionen mit Programmen, um umfangreichere Funktionalität bereitzustellen; Visual Studio ist es auch viel wie die Quellcodeverwaltungsfunktionen durchgeführt wird, die sie gemäß der Source-Plug-in-API erreicht wird, nicht wichtig.  
  
- Es ist einfacher, ein Quellcodeverwaltungs-Plug-in als ein Quellcodeverwaltungs-VSPackage implementiert.  
  
## <a name="source-control-vspackage"></a>Quellcodeverwaltungs-VSPackage  
 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] ermöglicht die umfassende Integration in Visual Studio in die vollständige Kontrolle der quellcodeverwaltung und die vollständige Ersetzung der Benutzeroberfläche der quellcodeverwaltung für Visual Studio bereitgestellten. Ein Datenquellen-Steuerelement VSPackage in Visual Studio registriert ist, und bietet Quellcodeverwaltungsfunktionen. Auch wenn mehrere Datenquellen-Steuerelement VSPackages mit Visual Studio registriert werden kann, kann nur einer von ihnen zu jedem Zeitpunkt aktiv sein. Ein Quellcodeverwaltungs-VSPackage hat vollständige Kontrolle über die quellcodeverwaltung und die Darstellung in Visual Studio, während es aktiv ist. Alle anderen Datenquellen-Steuerelement VSPackages, die möglicherweise im System registriert ist inaktiv sind, und es wird keine Benutzeroberfläche anzeigt überhaupt.  
  
 Implementierung eines Quellcodeverwaltungs-VSPackage ist eine Strategie für die "Alles oder nichts" erforderlich. Der Ersteller eines Quellcodeverwaltungs-VSPackage muss eine beträchtliche Menge an Aufwand bei der Implementierung einer Reihe von Steuerelement-Schnittstellen und neue Benutzeroberflächenelemente (Dialogfelder, Menüs und Symbolleisten) aus, um die gesamte Quellcodeverwaltungsfunktionen abzudecken investieren. Finden Sie unter [Erstellen eines Quellcodeverwaltungs-VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md) Weitere Details.  
  
### <a name="drawbacks-to-implementing-a-source-control-vspackage"></a>Nachteile der Implementierung eines Quellcodeverwaltungs-VSPackages  
  
- Das VSPackage muss es sich um eine Reihe von komplexen Schnittstellen für die erfolgreiche Integration in Visual Studio implementieren.  
  
- VSPackages muss die Benutzeroberfläche, die für die erforderlich sind, für die quellcodeverwaltung angeben; Visual Studio bietet keine Unterstützung in diesem Bereich.  
  
- Ein Datenquellen-Steuerelement das VSPackage in Visual Studio-Desktopplattform gebunden ist, und kann nicht verwendet werden eigenständige Programme, damit Funktionen einfach mit einer externen Version des Quellcode-Verwaltungsprogramm gemeinsam genutzt werden kann.  
  
### <a name="advantages-to-implementing-a-source-control-vspackage"></a>Vorteile für die Implementierung eines Quellcodeverwaltungs-VSPackages  
  
- Das VSPackage vollständige Kontrolle über die Benutzeroberfläche der quellcodeverwaltung und Funktionen verfügt, wird der Benutzer eine nahtlose Schnittstelle für die quellcodeverwaltung angezeigt.  
  
- Das VSPackage ist nicht auf einen bestimmten quellcodeverwaltungmodell beschränkt.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenquellen-Steuerelement](../../extensibility/internals/source-control.md)   
 [Erstellen eines Quellcodeverwaltungs-Plug-in](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Erstellen eines Quellcodeverwaltungs-VSPackages](../../extensibility/internals/creating-a-source-control-vspackage.md)   
 [Neuigkeiten in der Quellcodeverwaltung](../../extensibility/internals/what-s-new-in-source-control.md)
