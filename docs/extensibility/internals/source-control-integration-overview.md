---
title: "Übersicht über das Steuerelement Integration Datenquelle | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control [Visual Studio SDK], about source control
ms.assetid: 3a46e4eb-e677-49c3-8647-d927d035a19a
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: dd7b6a48b00e8bef62ff801519fc35cdc163902d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="source-control-integration-overview"></a>Übersicht über die Integration von Datenquellen-Steuerelement
In diesem Abschnitt werden die zwei Möglichkeiten zur Integration in Visual Studio-quellcodeverwaltung verglichen; ein Quellcodeverwaltungs-Plug-in und eines VSPackage, das eine Source Control-Lösung bietet und die neuen Funktionen der quellcodeverwaltung hervorgehoben. Visual Studio ermöglicht Manueller Wechsel zwischen den Datenquellen-Steuerelements VSPackages und Datenquellen-Steuerelement-Plug-ins als auch automatische Lösung basierenden Wechsel.  
  
## <a name="source-control-integration"></a>Integration der Quellcodeverwaltung  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]unterstützt zwei Arten von Quellcodeverwaltungsoptionen Integration. In allen Versionen von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], Sie können immer noch ein plug-in basierend auf der Quelle Steuerelement-Plug-in-API (zuvor auch bezeichnet als MSSCCI-API), die grundlegende Quellcodeverwaltungsfunktion bereitstellt, bei der Verwendung von Visual Studio Source Control Benutzer-Schnittstelle (integrieren UI). Ein Datenquellen-Steuerelement VSPackage, andererseits, eine neue, umfassende-Integration bietet [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Pfad für die Integration der quellcodeverwaltung, die eine hohe Wissensstand und Autonomie in seiner Steuerelement Quellmodell gefordert geeignet ist.  
  
 ![Übersicht über das Steuerelement Datenquelle](../../extensibility/internals/media/sourcectnrloverview.gif "SourceCtnrlOverview")  
  
## <a name="source-control-plug-in"></a>Datenquellen-Steuerelement-Plug-in  
 Alle Versionen von Visual Studio unterstützen die Quelle Steuerelement-Plug-in-API Spezifikationsversion 1.2 als Integration Pfad. Eine Quelle Steuerelement-Plug-in-Implementierung schreibt eine DLL, die die Quelle Steuerelement-Plug-in-API-Funktionen zur Integration der quellcodeverwaltung und Registrierung implementiert, wie in beschrieben [ein Datenquellen-Steuerelement-Plug-in erstellen](../../extensibility/internals/creating-a-source-control-plug-in.md). Bei diesem Ansatz die Umgebung IDE (Integrated Development) verwendet die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] UI für Dialogfelder, z. B. Einchecken, Auschecken, Extras/Optionen Eigenschaftenseiten, Symbolleisten und Source Control Symbole. Strenge Einhaltung der Datenquellen-Steuerelement-Plug-in-API ist eine einfache Integration in Visual Studio und eine problemlose praktisches Beispiel für die Benutzer sichergestellt. Dies bedeutet, dass die Datenquellen-Steuerelements, das plug-in implementieren muss, die meisten Funktionen und Rückrufe, die in der API beschrieben.  
  
 Gehen Sie folgendermaßen vor, um ein Quellcodeverwaltungs-Plug-in mithilfe der Datenquellen-Steuerelement-Plug-in-API zu implementieren:  
  
1.  Erstellen Sie eine DLL, die die angegebenen Funktionen implementiert [Quellcodeverwaltung-Plug-ins](../../extensibility/source-control-plug-ins.md).  
  
2.  Die DLL registrieren, indem Sie die Verfügbarkeit der zutreffenden Registrierungseinträge (beschrieben [Vorgehensweise: Installieren Sie eine Datenquellen-Steuerelement-Plug-in](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)).  
  
3.  Erstellen Sie eine Hilfsprogramm, Benutzeroberfläche und anzeigen, wenn Sie aufgefordert werden, von der Quelle Steuerelement Adapter-Paket (der Visual Studio-Komponente, verarbeitet der Quellcodeverwaltungsfunktion über Datenquellen-Steuerelement-Plug-ins)  
  
 Reaktion auf ein Datenquellen-Steuerelement-Befehl der Visual Studio-IDE stellt ein Standardoberfläche für die grundlegenden Vorgänge und übergibt dann die Informationen zu den Datenquellen-Steuerelement-Plug-in über die Funktionen, die in der Quelle Steuerelement-Plug-in-API definiert. Um erweiterte Optionen anzugeben kann die Datenquellen-Steuerelement-Plug-In für aufgerufen werden um eine eigene Benutzeroberfläche anzuzeigen, z. B. Suchen nach einem quellcodeverwalteten Projekt. Dies bedeutet, dass der Benutzer mit zwei möglicherweise verschiedene Formate der Benutzeroberfläche kann, beim Umgang mit quellcodeverwaltung angezeigt werden: die Benutzeroberfläche, in dem Visual Studio dargestellt und die Benutzeroberfläche, in dem das Quellsteuerelement-Plug-in dargestellt. Dies ist am deutlichsten für erweiterte Quellcodeverwaltungsvorgänge.  
  
### <a name="drawbacks-to-implementing-a-source-control-plug-in"></a>Nachteile der Implementierung ein Quellcodeverwaltungs-Plug-in  
  
-   Für erweiterte Funktionen möglicherweise der Benutzer zwei verschiedene Arten von Schnittstellen, was zu Verwechslungen.  
  
-   Die Datenquellen-Steuerelement-Plug-in ist auf das Steuerelement Quellmodell impliziert durch die Quelle Steuerelement-Plug-in-API beschränkt.  
  
-   Die Datenquellen-Steuerelement-Plug-in-API möglicherweise für bestimmte Steuerelementszenarien Quelle zu restriktiv.  
  
### <a name="advantages-to-implementing-a-source-control-plug-in"></a>Vorteile der Implementierung ein Quellcodeverwaltungs-Plug-in  
  
-   Visual Studio stellt keine Benutzeroberfläche für alle grundlegenden Quellcodeverwaltungsvorgänge, damit das Quellsteuerelement-Plug-in nicht potenziell komplexen UI implementieren.  
  
-   Aufgrund der strict-API kann die Datenquellen-Steuerelement-Plug-in leicht externen Quelle Steuerelement Benutzerinteraktionen mit Programmen, um eine erweiterte Funktionalität bereitzustellen; Visual Studio befasst sich nicht zu viel wie die Quellcodeverwaltungsfunktion erfolgt nur, die sie gemäß der Datenquellen-Steuerelement-Plug-in-API erfolgt, gezeigt.  
  
-   Es ist einfacher, ein Quellcodeverwaltungs-Plug-in als ein Datenquellen-Steuerelement VSPackage implementieren.  
  
## <a name="source-control-vspackage"></a>Source Control VSPackage  
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]enge Integration in Visual Studio mit Vollzugriff auf Quellcodeverwaltungsfunktion und die vollständige Ersetzung der Benutzeroberfläche der quellcodeverwaltung von Visual Studio bereitgestellten ermöglicht. Ein Datenquellen-Steuerelement VSPackage wird in Visual Studio registriert und Quellcodeverwaltungsfunktion bietet. Obwohl mehrere Datenquellen-Steuerelements VSPackages mit Visual Studio registriert werden kann, kann nur einer von ihnen gleichzeitig aktiv sein. Ein VSPackage des Datenquellen-Steuerelement hat vollständige Kontrolle über die Quellcodeverwaltungsfunktion und die Darstellung in Visual Studio, während er aktiv ist. Alle anderen Datenquellen-Steuerelements VSPackages, die möglicherweise im System registriert ist inaktiv sind, und zeigt keine Benutzeroberfläche überhaupt.  
  
 Implementieren ein VSPackage des Datenquellen-Steuerelement erfordert eine Strategie für die "" alle "oder" nichts ". Der Ersteller des ein Datenquellen-Steuerelement VSPackage muss eine beträchtliche Menge an Aufwand bei der Implementierung einer Reihe von Datenquellen-Steuerelement-Schnittstellen und neue Elemente der Benutzeroberfläche (Dialogfelder, Menüs und Symbolleisten), um die gesamte Quellcodeverwaltungsfunktion abzudecken investieren. Finden Sie unter [Erstellen eines Source Control VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md) Weitere Details.  
  
### <a name="drawbacks-to-implementing-a-source-control-vspackage"></a>Nachteile für die Implementierung einer Quelle Steuerelement VSPackages  
  
-   Eine Anzahl von komplexen Schnittstellen erfolgreich Integration in Visual Studio muss das VSPackage implementiert werden.  
  
-   Das VSPackage muss die Benutzeroberfläche, die erforderlich sind, für die quellcodeverwaltung angeben; Visual Studio bietet keine Unterstützung nach "in diesem Bereich.  
  
-   Ein Datenquellen-Steuerelement VSPackage zu Visual Studio-Desktopplattform gebunden ist und funktioniert nicht mit eigenständige Programme so Funktionalität mit einer externen Version des Quellcode-Verwaltungsprogramm genauso einfach gemeinsam genutzt werden kann.  
  
### <a name="advantages-to-implementing-a-source-control-vspackage"></a>Vorteile für die Implementierung einer Quelle Steuerelement VSPackages  
  
-   Da das VSPackage volle Kontrolle über die quellcodeverwaltung Benutzeroberfläche und Funktionalität hat, erhält der Benutzer eine nahtlose Oberfläche für die Datenquellen-Steuerelements.  
  
-   Das VSPackage ist nicht auf einem bestimmten Steuerelement Quellmodell beschränkt.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenquellen-Steuerelements](../../extensibility/internals/source-control.md)   
 [Erstellen ein Quellcodeverwaltungs-Plug-in](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Erstellen eines Source Control VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)   
 [Neuigkeiten in der Quellcodeverwaltung](../../extensibility/internals/what-s-new-in-source-control.md)