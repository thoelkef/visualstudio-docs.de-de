---
title: "&#220;bersicht &#252;ber die Integration von Datenquellen-Steuerelement | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Datenquellen-Steuerelement [Visual Studio SDK] zum Datenquellen-Steuerelement"
ms.assetid: 3a46e4eb-e677-49c3-8647-d927d035a19a
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# &#220;bersicht &#252;ber die Integration von Datenquellen-Steuerelement
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In diesem Abschnitt werden die beiden Möglichkeiten, Visual Studio\-Quellcodeverwaltung zu integrieren. ein Quellcodeverwaltungs\-Plug\-In und VSPackages, das eine Projektmappe der Quellcodeverwaltung bietet und die neuen Funktionen zur Quellcodeverwaltung hervorhebt.  Visual Studio können manuelle den Wechsel zwischen steckverbindungen Quellcodeverwaltung und VSPackages Quellcodeverwaltung sowie die automatische Projektmappe\-basierte den Wechsel zu.  
  
## Quellcodeverwaltungsintegration  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] unterstützt zwei Arten von Optionen Quellcodeverwaltungsintegrations.  In allen Versionen von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], können Sie ein Plug\-In auf das Quellcodeverwaltungs\-Plug\-In API zuvor noch integrieren \(auch bezeichnet als MSSCCI APIs\), das grundlegende Funktionen für Quellcodeverwaltung bei der Verwendung der Visual Studio\-Quellcodeverwaltungs Benutzeroberfläche bereitstellt.  Eine Quellcodeverwaltung VSPackage stellt dagegen eine neue [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Integration. Quellcodeverwaltungsintegration für geeignet ist, die eine hohe Ebene der Kultiviertheit Autonomie und der Quellcodeverwaltung im Modell erfordert.  
  
 ![Übersicht über die Quellcodeverwaltung](~/docs/extensibility/internals/media/sourcectnrloverview.gif "SourceCtnrlOverview")  
  
## Quellcodeverwaltungs\-Plug\-In  
 Alle Versionen von Visual Studio unterstützen die Spezifikationsversion des 1.2 des Quellcodeverwaltungs\-Plug\-In Integrations API als Pfad.  Eine Quellcodeverwaltungs\-Plug\-In\-Implementierung schreibt eine DLL, die die Quellcodeverwaltungs\-Plug\-In\-API\-Funktionen für Quellcodeverwaltungsintegration und Registrierung implementiert, z. B. in [Erstellen ein Quellcodeverwaltungs\-Plug\-in](../../extensibility/internals/creating-a-source-control-plug-in.md)beschrieben.  In diesem Verfahren wird die integrierte Entwicklungsumgebung \(IDE\), das [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Benutzeroberfläche für Dialogfelder, wie überprüft in Auschecken, Tools\/Optionen unter Quellcodeverwaltung Eigenschaftenseiten, Symbolleisten und Symbole.  Strenge Zugehörigkeit in das Quellcodeverwaltungs\-Plug\-In API versichert eine einfache Integration in Visual Studio und eine störungsfreie Erfahrung für den Benutzer.  Dies bedeutet, dass das Quellcodeverwaltungs\-Plug\-In die meisten Funktionen und Rückrufe implementieren muss, die im API einzeln aufgelistet sind.  
  
 Um ein Quellcodeverwaltungs\-Plug\-In mit dem Quellcodeverwaltungs\-Plug\-In API zu implementieren, führen Sie folgende Schritte aus:  
  
1.  Erstellen Sie eine DLL, die die Features implementiert, die in [Source Control\-Plug\-ins](../../extensibility/source-control-plug-ins.md)angegeben werden.  
  
2.  Registrieren Sie die DLL, indem Sie die entsprechenden Registrierungseinträge ausführen \(beschrieben in [Gewusst wie: Installieren Sie ein Quellcodeverwaltungs\-Plug\-in](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)\).  
  
3.  Erstellen Sie eine Hilfe Benutzeroberfläche und zeigen Sie an, wann \(die vom aufgefordert Quellcodeverwaltungs\-Adapter\-Paket Visual Studio\-Komponente, die steckverbindungen Quellcodeverwaltung über die Quellcodeverwaltung behandelt\)  
  
 Als Reaktion auf einen Befehl Quellcodeverwaltung stellt die Visual Studio\-IDE eine standardmäßige Benutzeroberfläche für die grundlegenden Vorgänge dar und übergibt dann die Informationen für das Quellcodeverwaltungs\-Plug\-In über die Funktionen, die im Quellcodeverwaltungs\-Plug\-In APIs definiert sind.  Für erweiterte Optionen können Sie das Quellcodeverwaltungs\-Plug\-In wird möglicherweise aufgerufen, um dem eigenen Benutzeroberfläche für ein Projekt beispielsweise der Quellcodeverwaltung unterliegen Durchsuchen darzustellen.  Dies bedeutet, dass der Benutzer möglicherweise mit zwei verschiedenen Formaten der Benutzeroberfläche dargestellt wird, wenn die Quellcodeverwaltung arbeiten: Das Benutzeroberflächenelement, das Visual Studio darstellt und die Benutzeroberfläche, das das Quellcodeverwaltungs\-Plug\-In darstellt.  Dies ist mit erweiterten Quellcodeverwaltungsvorgängen am beträchtlichsten.  
  
### Nachteile zum Implementieren eines Quellcodeverwaltungs\-Plug\-In  
  
-   Für erweiterte Features sieht der Benutzer zwei unterschiedliche Formate Schnittstellen und wird standardmäßig auf mögliche Probleme.  
  
-   Das Modell der Quellcodeverwaltung wird für das Quellcodeverwaltungs\-Plug\-In begrenzt, das durch das Quellcodeverwaltungs\-Plug\-In APIs vorgesehen ist.  
  
-   Das Quellcodeverwaltungs\-Plug\-In API ist möglicherweise bei einigen Szenarios Quellcodeverwaltung zu restriktiv.  
  
### Vorteile zum Implementieren eines Quellcodeverwaltungs\-Plug\-In  
  
-   Visual Studio\-Zubehör alle Benutzeroberfläche für alle grundlegenden Quellcodeverwaltungsvorgänge, für das Quellcodeverwaltungs\-Plug\-In potenziell komplexen Benutzeroberfläche implementieren muss.  
  
-   Aufgrund des strengen API kann das Quellcodeverwaltungs\-Plug\-In mit externen Quelle kontrollprogrammen interagieren kann, um verbesserte Funktionalität bereitzustellen. Visual Studio berücksichtigt nicht zu viele Funktionen, z. B. die Quellcodeverwaltung erreicht ist, werden nur die es entsprechend dem Quellcodeverwaltungs\-Plug\-In API erreicht ist.  
  
-   Es ist einfacher, ein Quellcodeverwaltungs\-Plug\-In als eine Quellcodeverwaltung VSPackage implementieren.  
  
## Quellcodeverwaltung VSPackage  
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] können tiefe Integration in Visual Studio Kontrolle der Quellcodeverwaltung mit Funktionen und vollständiger Ersatz Visuals Studio\-stellte Benutzeroberfläche der Quellcodeverwaltung bereit.  Eine Quellcodeverwaltung VSPackage wird mit Visual Studio registriert und stellt Funktionen für Quellcodeverwaltung.  Obwohl einige Quellcodeverwaltung VSPackages mit Visual Studio registriert werden kann, nur einer der XML\-Strukturen zu jeder Zeit aktiv sein können.  Eine Quellcodeverwaltung VSPackage ist die vollständige Kontrolle über die Quellcodeverwaltung Funktionen und Darstellung in Visual Studio, während sie aktiv ist.  Alle VSPackages Quellcodeverwaltung, die sich im System registriert wird, ist inaktiv. Es wird keine Benutzeroberfläche überhaupt angezeigt werden.  
  
 Die Implementierung einer Quellcodeverwaltung VSPackage erfordert „Nothing“ Strategie oder legt diese fest.  Der Ersteller einer Quellcodeverwaltung für eine große Menge an Mehraufwand muss ein VSPackage investieren, wenn er mehrere Schnittstellen Quellcodeverwaltung und neuer Benutzeroberflächenelemente \(Dialogfelder, Menüs und Symbolleisten\) implementiert, um die gesamte Funktionalität der Quellcodeverwaltung eingeschlossen werden sollen.  Ausführliche Informationen finden Sie unter [Erstellen eines VSPackages Datenquellen\-Steuerelement](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
### Nachteile zum Implementieren einer Quellcodeverwaltung VSPackage  
  
-   VSPackage muss mehrere komplexe Schnittstellen implementieren, um mit Visual Studio erfolgreich zu integrieren.  
  
-   VSPackage muss alle Benutzeroberfläche angeben, das für die Quellcodeverwaltung erforderlich ist. Visual Studio bietet keine Unterstützung in diesem Bereich.  
  
-   Eine Quellcodeverwaltung VSPackages Visual Studio vertraut wird am gebunden und kann nicht mit eigenständigen Programmen ausgeführt, sodass der Funktionalität nicht einfach freigegeben sein mit einer externen Version des programms Quellcodeverwaltung.  
  
### Vorteile zum Implementieren einer Quellcodeverwaltung VSPackage  
  
-   Da ein VSPackage Kontrolle über die Quellcodeverwaltung Benutzeroberfläche und Funktionen verfügt, wird der Benutzer mit einer nahtlosen Schnittstelle für die Quellcodeverwaltung dargestellt.  
  
-   VSPackage wird nicht in einem bestimmten Modell der Quellcodeverwaltung begrenzt.  
  
## Siehe auch  
 [Quellcodeverwaltung](../../extensibility/internals/source-control.md)   
 [Erstellen ein Quellcodeverwaltungs\-Plug\-in](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Erstellen eines VSPackages Datenquellen\-Steuerelement](../../extensibility/internals/creating-a-source-control-vspackage.md)   
 [Was ist neu im Datenquellen\-Steuerelement](../../extensibility/internals/what-s-new-in-source-control.md)