---
title: Windows Installer-Grundlagen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows Installer, VSPackages
- VSPackages, Windows Installer basics
ms.assetid: 497e479b-add8-4644-870a-917f15306b97
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 23f633b57a677996a5f286ca1f5ac4b911b3cdda
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49829312"
---
# <a name="windows-installer-basics"></a>Grundlagen zu Windows Installer
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Das Windows-Installationsprogramm installiert und deinstalliert, Anwendungen oder Softwareprodukte auf dem Computer eines Benutzers, Ausführen dieser Aufgaben in so genannten Windows Installer-Komponenten (manchmal als WICs oder nur Komponenten bezeichnet). Eine GUID identifiziert jedes WIC, die die grundlegende Einheit der Installation und die verweiszählung für Einrichtungen, die mit Windows Installer ist.  
  
 Umfassende Dokumentation zu den Windows Installer, finden Sie unter dem Thema Platform SDK [Windows Installer](http://msdn.microsoft.com/library/aa372866.aspx).  
  
## <a name="authoring-a-vspackage"></a>Erstellen eine VSPackage  
 Windows Installer verwendet Installationspakete, die Informationen, die Windows Installer installieren enthalten, deinstallieren oder Reparieren eines Produkts und die Setup-Benutzeroberfläche (UI) ausführen. Jedem Installationspaket enthält eine MSI-Datei, die eine Installationsdatenbank, einen Stream zusammenfassende Informationen und Datenströme für die verschiedenen Teilen der Installation enthält. Um das Installationsprogramm zu verwenden, müssen Sie eine Installation erstellen. Da das Installationsprogramm Installationen auf dem Konzept von Komponenten organisiert und Informationen zur Installation in einer relationalen Datenbank speichert, umfasst der Prozess der Erstellung von einem Installationspaket Allgemein die folgenden Schritte aus:  
  
1. Planen Sie Ihr Setup erstellen, um Ihrer Seite-an-Seite-Strategien und versionsverwaltung zu unterstützen.  
  
2. Identifizieren Sie die Funktionen, die Benutzern angezeigt werden.  
  
3. Organisieren Sie das VSPackage und Abhängigkeiten in Komponenten.  
  
4. Füllen Sie die Installationsdatenbank mit Informationen.  
  
5. Überprüfen Sie das Installationspaket ein.  
  
   Diese Dokumentation ist in erster Linie mit der erste und dritte Schritt des Prozesses befasst. Beim Ausführen dieser Schritte Sie organisieren Sie Ihre VSPackage-Funktionen in WICs, damit Sie Ihre versionsverwaltung und Wartung von Strategie zum Konto für nachfolgende Versionen der frame können [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Die verbleibenden drei Schritte werden in der Dokumentation zu Windows Installer im Platform SDK ausführlich behandelt.  
  
## <a name="key-terms"></a>Wichtige Begriffe  
 Folgendes sind Definitionen der wichtigsten Begriffe im Zusammenhang mit der Windows Installer-Technologie.  
  
 Ressource  
 Dateien, Registrierungsschlüssel, Verknüpfungen oder und so weiter, die auf einem Computer installiert werden kann. Diese Ressourcen werden in der Windows Installer-Komponenten logisch gruppiert.  
  
 Windows Installer-Komponente (WIC)  
 Die grundlegende Einheit der Installation, die eine logische Gruppierung von verwandten Ressourcen, die installiert und deinstalliert werden, als eine Einheit darstellt. Windows Installer-Komponenten werden durch eine eindeutige Komponenten-ID oder GUID identifiziert. Windows Installer verwaltet außerdem die verweiszählung, die auf der WIC-Ebene. Flexibilität erhalten Sie maximale versionsverwaltung schließen Sie nicht mehr als einen primäre Ressource, z. B. eine DLL in einer bestimmten WIC ein. Beachten Sie, nachdem Sie identifizieren und füllen Sie einen WIC, weisen Sie ihm eine GUID und bereitstellen, können Sie die Zusammensetzung ändern. Weitere Informationen finden Sie unter [Organisieren von Anwendungen in Komponenten](http://msdn.microsoft.com/library/aa370561.aspx).  
  
 Paket (Redist-Paket)  
 Eine Einheit der Bereitstellung, die besteht aus einer MSI-Datei und externen Quelldateien auf denen diese Datei verweisen kann. Ein Paket enthält alle Informationen, die Windows Installer benötigt, um die Benutzeroberfläche auszuführen und zu installieren oder deinstallieren die Anwendung.  
  
 MSI-Datei  
 Eine COM-strukturierter Speicher-Datei, die Anweisungen und die Daten, die zur Installation einer Anwendungs erforderlich sind. Jedes Paket enthält mindestens eine MSI-Datei. Die MSI-Datei enthält die Installer-Datenbank, einen Stream Zusammenfassungsinformationen, und möglicherweise eine oder mehrere Transformationen und interne Quelldateien. Zu installierenden Dateien können entweder werden in CAB-Datei komprimiert und in einem Datenstrom in die MSI-Datei gespeichert oder gespeichert, komprimiert oder unkomprimiert, außerhalb der MSI-Datei auf dem Quellmedium. Weitere Informationen finden Sie unter [Windows Installer-Dateierweiterungen](http://msdn.microsoft.com/library/aa372842\(VS.85\).aspx).  
  
## <a name="windows-installer-rules-enforcement"></a>Windows Installer-Regelerzwingung  
 Zwei Sätze von Regeln bestimmen, die Bereitstellung von Ressourcen durch das Setup Komponenten. Ein Regelsatz wird durch die Windows-Installer selbst verwaltet, während Sie die zweite Gruppe als Installation Autor erzwingen soll.  
  
> [!NOTE]
>  Erzwingung von Windows Installer-Regeln tritt nur dann, wenn Sie eine Überprüfung der MSI-Datei ausführen. Dennoch sind Sie hingewiesen, um diese Regeln als bewährte Methoden zu behandeln. Weitere Informationen finden Sie unter [Überprüfen einer Installationsdatenbank](http://msdn.microsoft.com/library/aa372477\(VS.85\).aspx) und [Paketüberprüfung](http://msdn.microsoft.com/library/aa370569\(VS.85\).aspx).  
  
#### <a name="installer-enforced-rules"></a>Erzwungene Installer-Regeln  
  
-   Alle Dateien in einer bestimmten Komponente müssen in dasselbe Verzeichnis installiert sein. Im Gegensatz dazu müssen separate Ordner installierte Dateien gehören, um Komponenten zu trennen.  
  
-   Es können nur ein Pfad pro Komponente vorhanden sein. Der Schlüsselpfad ist einfach eine Datei oder einen Registrierungsschlüssel Schlüssel, der die ganze Komponente darstellt.  
  
#### <a name="component-provider-responsibilities"></a>Komponentenanbieter Aufgaben  
  
-   Alle zwei Ressourcen, die getrennt in zukünftigen Versionen ausgeliefert werden können, sollte in separate Komponenten vorhanden sein. Ressourcen sollten in der gleichen Komponente gruppiert werden, nur, wenn Sie sicher sind, dass diese Ressourcen getrennt nie ausgeliefert werden. Es wird in der Tat empfohlen, alle primären Ressourcen (z. B. DLLs) in separaten WICs vorhanden sein. Weitere Informationen finden Sie unter [Installationsprogrammkomponenten definieren](http://msdn.microsoft.com/library/aa368269\(VS.85\).aspx).  
  
-   Keine Ressource mit versionsverwaltung durch das sollte jemals in mehr als ein WIC liefern.  
  
## <a name="see-also"></a>Siehe auch  
 [Was geschieht, wenn die Komponentenregeln unterbrochen werden?](http://msdn.microsoft.com/library/aa372795\(VS.85\).aspx)

