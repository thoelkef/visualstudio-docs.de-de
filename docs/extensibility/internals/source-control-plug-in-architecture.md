---
title: Source Control Plug-in-Architektur | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control plug-ins, architecture
ms.assetid: 35351d4c-9414-409b-98fc-f2023e2426b7
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e0cde4ca360aa0059abcbe0b64d63b4a94e85d78
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="source-control-plug-in-architecture"></a>Source Control Plug-in-Architektur
Sie können die Unterstützung des Datenquellen-Steuerelement zum Hinzufügen der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung (IDE) durch Implementieren und ein Quellcodeverwaltungs-Plug-in anfügen. Die IDE eine Verbindung mit dem Datenquellen-Steuerelement-Plug-in über die klar definierte Source Control-Plug-in-API. Die IDE macht Funktionen für die Version von dem Quellcodeverwaltungssystem durch Bereitstellen einer Benutzeroberfläche (UI), die der Symbolleisten und Befehle im Menü besteht. Die Datenquellen-Steuerelement-Plug-in implementiert die Quellcodeverwaltungsfunktion.  
  
## <a name="source-control-plug-in-resources"></a>Plug-in-Quelle Steuerung von Ressourcen  
 Die Datenquellen-Steuerelement-Plug-in enthält Ressourcen, die beim Erstellen und verbinden Sie die Anwendung Versioning unterstützen die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Die Datenquellen-Steuerelement-Plug-in enthält die API-Spezifikation, die durch ein Quellcodeverwaltungs-Plug-in implementiert werden muss, damit er in integriert werden kann die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Außerdem enthält ein Codebeispiel (in C++ geschriebene), die eine Skelett Source Steuerelement-Plug-in zeigt-Implementierung der Hauptfunktionen, die kompatibel mit der Source Control-Plug-in-API implementiert.  
  
 Die Datenquellen-Steuerelement-Plug-in API-Spezifikation können Sie einem beliebigen Quellcodeverwaltungssystem Ihrer Wahl zu nutzen, wenn ein Quellcodeverwaltungs-DLL zu, mit dem erforderlichen Satz von Funktionen, die in Übereinstimmung mit der Quelle Steuerelement-Plug-in-API implementiert erstellen.  
  
## <a name="components"></a>Komponenten  
 Das Quellcodeverwaltungspaket Adapter im Diagramm ist die Komponente der IDE, der die Anforderung des Benutzers für eine Quelle-Steuerungsvorgang in einem Funktionsaufruf, der von der quellcodeverwaltung-Plug-in unterstützt übersetzt. Damit dies der Fall sein benötigen die IDE und die Datenquellen-Steuerelement-Plug-in einen effektiven Dialog, der Informationen zwischen der IDE und des Plug-Ins hin-und übergibt. Für diesen Dialog erfolgen müssen beide dieselbe Sprache verwenden. Die Quell-Plug-in-API mit dem in dieser Dokumentation beschriebenen ist die Allgemeines Vokabular für diesen Austausch an.  
  
 ![Source-Architekturdiagramm](../../extensibility/internals/media/vs_sccsdk_plug_in_arch.gif "Vs_sccsdk_plug_in_arch")  
Architekturdiagramm mit Interaktion zwischen VS und Datenquellen-Steuerelement-Plug-in  
  
 Im Architekturdiagramm, entsprechend der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Shell, mit der Bezeichnung als VS Shell im Diagramm hostet, funktionierende Projekte und die zugehörigen Komponenten, z. B. die Editoren und Projektmappen-Explorer des Benutzers. Das Quellcodeverwaltungspaket-Adapter behandelt die Interaktion zwischen der IDE und die Datenquellen-Steuerelement-Plug-in. Das Quellcodeverwaltungspaket-Adapter stellt eine eigene Benutzeroberfläche des Datenquellen-Steuerelements bereit. Es ist die auf der obersten Ebene Benutzeroberfläche, die der Benutzer interagiert, um initiieren, und legen Sie den Projektumfang ein Quelle-Steuerungsvorgang.  
  
 Die Datenquellen-Steuerelement-Plug-in kann eine eigene Benutzeroberfläche haben zwei Teilen bestehen kann, wie in der Abbildung dargestellt. Feld mit der Bezeichnung "Hersteller UI" stellt benutzerdefinierte Benutzeroberflächenelemente, die Sie als Quelle Steuerelement-Plug-in Ersteller, bereitstellen. Diese werden direkt von der quellcodeverwaltung-Plug-in angezeigt, wenn der Benutzer einen erweiterten Quelle-Steuerungsvorgang aufruft. Feld mit der Bezeichnung "Hilfsprogramm-UI" ist ein Satz Source Control-Plug-in von Features der Benutzeroberfläche, die indirekt über die IDE aufgerufen werden. Die Datenquellen-Steuerelement-Plug-in übergeben UI-bezogene Nachrichten der IDE über spezielle Fehlerrückruf-Funktionen, die von der IDE bereitgestellt. Der Hilfsprogramm-UI ermöglicht eine nahtlosere Integration mit der IDE (häufig durch die Verwendung der ein **erweitert** Schaltfläche) und bietet somit eine einheitliche endbenutzererfahrung.  
  
 Ein Quellcodeverwaltungs-Plug-in kann keine Änderungen vornehmen, um die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] shell auf, und daher das Quellcodeverwaltungspaket-Adapter oder die Quelle steuern Benutzeroberfläche, die von der IDE bereitgestellt. Es muss nutzen, maximale Flexibilität, der durch die Implementierung des verschiedene Datenquellen-Steuerelement-Plug-in-API-Funktionen, die auf eine integrierte Lösung für den Endbenutzer beitragen. Der Abschnitt "Referenz" der Datenquellen-Steuerelement-Plug-in API-Dokumentation enthält Informationen für einige erweiterte Datenquellen-Steuerelement-Plug-in-Funktionen. Um diese Funktionen nutzen zu können, muss die Datenquellen-Steuerelement-Plug-in den erweiterten Funktionen der IDE während der Initialisierung deklarieren, und sie müssen bestimmte erweiterte Funktionen für jede Funktion implementiert.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenquellen-Steuerelement-Plug-ins](../../extensibility/source-control-plug-ins.md)   
 [Glossar](../../extensibility/source-control-plug-in-glossary.md)   
 [Erstellen eines Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/creating-a-source-control-plug-in.md)