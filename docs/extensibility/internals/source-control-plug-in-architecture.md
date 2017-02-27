---
title: "Source Control Plug-in-Architektur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Source Control-Plug-ins Architektur"
ms.assetid: 35351d4c-9414-409b-98fc-f2023e2426b7
caps.latest.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 24
---
# Source Control Plug-in-Architektur
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Sie können Unterstützung für die Quellcodeverwaltung [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] der integrierten Entwicklungsumgebung \(IDE\) indem Sie ein Quellcodeverwaltungs\-Plug\-In hinzufügen implementieren und anfügen.  Die IDE stellt eine Verbindung über das Quellcodeverwaltungs\-Plug\-In das Quellcodeverwaltungs\-Plug\-In klar definierte APIs an.  Die IDE macht die Funktionen der Versionskontrolle des Quellcodeverwaltungssystems, indem eine Benutzeroberfläche bereitstellt, die Symbolleisten und Menübefehlen besteht.  Das Quellcodeverwaltungs\-Plug\-In implementiert die Quellcodeverwaltung.  
  
## Quellcodeverwaltungs\-Plug\-In\-Betriebsmittel  
 Das Quellcodeverwaltungs\-Plug\-In stellt Ressourcen bereit, um die Versionsverwaltungs\-Anwendung an das [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE zu erstellen und zu verbinden.  Das Quellcodeverwaltungs\-Plug\-In enthält die API\-Spezifikation, die durch ein Quellcodeverwaltungs\-Plug\-In implementiert werden muss, damit es in das [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE integriert werden kann.  Sie enthält außerdem ein Codebeispiel \(geschrieben in C\+\+\) implementiert ein Skelett quellcodeverwaltungs\-plug\-in, das den wichtigsten Features der Implementierung veranschaulicht, die mit dem Quellcodeverwaltungs\-Plug\-In APIs kompatibel sind.  
  
 Die Spezifikation des Quellcodeverwaltungs\-Plug\-In API können Sie ein Quellcodeverwaltungssystem der Auswahl der Quellcodeverwaltung nutzen, wenn Sie eine DLL mit dem erforderlichen Satz von Funktionen erstellen, die in Übereinstimmung mit dem Quellcodeverwaltungs\-Plug\-In API implementiert werden.  
  
## Komponenten  
 Das Quellcodeverwaltungs\-Adapter\-Paket im Diagramm werden die Komponente der IDE, das die Benutzeranforderung für einen Quellcodeverwaltungsvorgang in einen Funktionsaufruf übersetzt, der durch das Quellcodeverwaltungs\-Plug\-In unterstützt wird.  Damit dies, die IDE und das Quellcodeverwaltungs\-Plug\-In muss ein effektives Dialogfeld, das Informationen über hin und her zwischen die IDE und das Plug\-In übergibt.  Damit dieses Dialogfeld stattfindet, müssen beide dieselbe Sprache sprechen.  Das Quellcodeverwaltungs\-Plug\-In API, die in dieser Dokumentation erläutert wird, ist das allgemeine Vokabular für den Austausch.  
  
 ![Quellcodeverwaltung&#45;Architekturdiagramm](../../extensibility/internals/media/vs_sccsdk_plug_in_arch.png "vs\_sccsdk\_plug\_in\_arch")  
Architektur\-Diagramm mit interaktion zwischen GEGEN und Quellcodeverwaltungs\-Plug\-In  
  
 Wie im Diagramm Architektur der Shell [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Bezeichnung gezeigt, wie GEGEN Shell im Diagramm den Hosts in der Arbeitsprojekte des Benutzers und in den zugehörigen Komponenten wie Editoren und dem Projektmappen\-Explorer.  Das Quellcodeverwaltungs\-Adapter\-Paket behandelt die Interaktion zwischen dem IDE und das Quellcodeverwaltungs\-Plug\-In.  Das Quellcodeverwaltungs\-Adapter\-Paket stellt eine eigene Benutzeroberfläche für die Quellcodeverwaltung.  Es handelt sich um die Benutzeroberfläche der obersten Ebene, dass der Benutzer interagiert, um den Bereich eines Quellcodeverwaltungsvorgangs zu starten und zu definieren.  
  
 Das Quellcodeverwaltungs\-Plug\-In kann über eine eigene Benutzeroberfläche verfügen, die aus zwei Teilen wie in der Abbildung gezeigt, besteht.  Das Feld mit dem Namen „Anbieter“ UI bezeichnet werden, stellt benutzerdefinierte Benutzeroberflächenelemente dar, die Sie als Quellcodeverwaltungs\-Plug\-In\-Ersteller, bereitstellen.  Diese werden direkt durch das Quellcodeverwaltungs\-Plug\-In angezeigt, wenn der Benutzer einen erweiterten Quellcodeverwaltungsvorgang aufruft.  Das Feld, das die Benutzeroberfläche „Hilfe“ beschriftet ist, ist eine Reihe von Funktionen des Quellcodeverwaltungs\-Plug\-In Benutzeroberfläche, die indirekt über die IDE aufgerufen werden.  Das Benutzeroberfläche\-verknüpfte Quellcodeverwaltungs\-Plug\-In leitet Nachrichten an die IDE durch die speziellen Rückruffunktionen weiter, die in der IDE bereitgestellt werden.  Die Hilfe Benutzeroberfläche erleichtert eine nahtlosere Integration mit der IDE \(meist durch die Verwendung einer **Erweitert** Schaltfläche\) und bietet somit eine einheitlichere Endbenutzer Darstellung.  
  
 Ein Quellcodeverwaltungs\-Plug\-In kann Änderungen an der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Shell und infolgedessen entweder am Quellcodeverwaltungs\-Adapter\-Paket bzw. der Quellcodeverwaltung Benutzeroberfläche nicht vornehmen, die in der IDE bereitgestellt werden.  Sie muss maximale Auslastung der Flexibilität machen, die durch die Implementierung von verschiedenen Quellcodeverwaltungs\-Plug\-In\-API\-Funktionen bereitgestellt wird, die zu einer integrierten Erfahrung für den Endbenutzer beitragen.  Das Referenzteil der Dokumentation des Quellcodeverwaltungs\-Plug\-In API enthält Informationen für einige erweiterte Quellcodeverwaltungs\-Plug\-In\-Funktionen.  Um diese Features zu verwenden, muss das Quellcodeverwaltungs\-Plug\-In die erweiterten Features zur IDE während der Initialisierung deklarieren, und sie muss bestimmten Erweiterte Features für jede Funktion implementieren.  
  
## Siehe auch  
 [Source Control\-Plug\-ins](../../extensibility/source-control-plug-ins.md)   
 [Glossar](../../extensibility/source-control-plug-in-glossary.md)   
 [Erstellen ein Quellcodeverwaltungs\-Plug\-in](../../extensibility/internals/creating-a-source-control-plug-in.md)