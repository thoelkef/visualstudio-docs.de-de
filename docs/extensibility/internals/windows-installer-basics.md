---
title: "Windows Installer-Grundlagen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Windows Installer, VSPackages"
  - "VSPackages, Windows Installer-Grundlagen"
ms.assetid: 497e479b-add8-4644-870a-917f15306b97
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Windows Installer-Grundlagen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Windows Installer installiert und deinstalliert Applikationen oder Software\-Produkte auf dem Computer eines Benutzers, diese Aufgaben in so genannten Windows Installer\-Komponenten \(auch WICs oder nur Komponenten bezeichnet\). Eine GUID identifiziert jedes WIC, die die grundlegende Einheit der Installations\- und verweiszählung für Installationen von Windows Installer ist.  
  
 Umfassende Dokumentation zu Windows Installer finden Sie unter dem Plattform\-SDK\-Thema [Windows Installer](http://msdn.microsoft.com/library/aa372866.aspx).  
  
## Erstellen ein VSPackage  
 Windows Installer verwendet Installationspakete, die Informationen, die Windows Installer enthalten zu installieren, deinstallieren oder reparieren ein Produkts und der Setup\-Benutzeroberfläche \(UI\) ausführen. Jedes Installationspaket umfasst eine MSI\-Datei, die eine Installationsdatenbank, einen Stream zusammenfassende Informationen und Datenströme für verschiedene Teile der Installation enthält. Um das Installationsprogramm zu verwenden, müssen Sie eine Installation erstellen. Da das Installationsprogramm Installationen auf dem Konzept von Komponenten organisiert und Informationen über die Installation in einer relationalen Datenbank speichert, umfasst der Prozess erstellen Sie ein Installationspaket Allgemein die folgenden Schritte aus:  
  
1.  Planen Sie Ihr Setup erstellen, die zur Unterstützung der Versionskontrolle und Side\-by\-Side\-Strategien.  
  
2.  Identifizieren Sie die Funktionen, die Benutzern angezeigt werden soll.  
  
3.  Ordnen Sie die VSPackage und Abhängigkeiten in Komponenten.  
  
4.  Die Installationsdatenbank mit Informationen aufgefüllt.  
  
5.  Überprüfen Sie das Installationspaket.  
  
 Diese Dokumentation ist in erster Linie mit der erste und dritte Schritt des Prozesses befasst. Beim Ausführen dieser Schritte Sie VSPackage Features in WICs so organisieren Sie Ihre Versionierung und Aktualisierungsstrategie zum Konto für nachfolgende Versionen der frame können [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Die verbleibenden drei Schritte sind in der Windows Installer\-Dokumentation im Plattform\-SDK ausführlich behandelt.  
  
## Wichtige Begriffe  
 Folgendes sind die Definitionen der wichtigsten Begriffe im Zusammenhang mit der Windows Installer\-Technologie.  
  
 Ressource  
 Dateien, Registrierungsschlüssel, Verknüpfungen oder usw., die auf einem Computer installiert werden kann. Diese Ressourcen werden in Windows Installer\-Komponenten logisch zusammengefasst werden.  
  
 Windows Installer\-Komponente \(WIC\)  
 Die grundlegende Einheit der Installation, die eine logische Gruppierung von verwandten Ressourcen, die installiert und deinstalliert als eine Einheit darstellt. Windows Installer\-Komponenten werden durch eine eindeutige Komponenten\-ID oder GUID identifiziert. Windows Installer verwaltet außerdem die Ebene der WIC zählen von verweisen. Versionskontrolle maximale Flexibilität erhalten Sie schließen Sie nicht mehr als eine primäre Ressource, z. B. eine DLL in einer bestimmten WIC. Beachten Sie, dass Sie nach dem identifizieren und einen WIC aufzufüllen, sie eine GUID geben und Bereitstellen der Komposition ändern können. Weitere Informationen finden Sie unter [Organizing Applications in Komponenten](http://msdn.microsoft.com/library/aa370561.aspx).  
  
 Paket \(Redist\-Paket\)  
 Eine Einheit der Bereitstellung, die auf die Datei zeigen möglicherweise eine MSI\-Datei und externen Quelldateien besteht. Ein Paket enthält alle Informationen, die Windows Installer zum Ausführen der Benutzeroberfläche und zum Installieren oder Deinstallieren der Anwendung benötigt.  
  
 MSI\-Datei  
 Eine COM\-strukturierter Speicher\-Datei, die die Anweisungen und die Installation eine Anwendung erforderlichen Daten enthält. Jedes Paket enthält mindestens eine MSI\-Datei. Die MSI\-Datei enthält die Installer\-Datenbank, einem Stream zusammenfassende Informationen und möglicherweise eine oder mehrere Transformationen und interne Quelldateien. Zu installierenden Dateien können entweder in eine CAB\-Datei komprimiert und in einen Stream in der MSI\-Datei gespeichert oder gespeichert, komprimiert oder dekomprimiert, außerhalb der MSI\-Datei auf das Quellmedium. Weitere Informationen finden Sie unter [Erweiterungen für Windows Installer](http://msdn.microsoft.com/library/aa372842\(VS.85\).aspx).  
  
## Windows Installer\-Regelerzwingung  
 Zwei Sätze von Regeln bestimmen die Bereitstellung von Ressourcen über die Setup\-Komponenten. Ein Regelsatz ist von der Windows\-Installer selbst beibehalten, während Sie die zweite Gruppe als Autor Installation erzwingen soll.  
  
> [!NOTE]
>  Erzwingung von Windows Installer\-Regeln erfolgt nur, wenn Sie eine Überprüfung der MSI\-Datei ausgeführt. Dennoch werden Sie diese Regeln als bewährte Methoden behandeln hingewiesen. Weitere Informationen finden Sie unter [Überprüfen einer Installationsdatenbank](http://msdn.microsoft.com/library/aa372477\(VS.85\).aspx) und [Paketüberprüfung](http://msdn.microsoft.com/library/aa370569\(VS.85\).aspx).  
  
#### Installer erzwungene Regeln  
  
-   Alle Dateien in einer bestimmten Komponente müssen im selben Verzeichnis installiert sein. Umgekehrt müssen separate Ordner installierte Dateien gehören, um Komponenten zu trennen.  
  
-   Es kann nur ein Schlüsselpfad pro Komponente vorhanden sein. Der Pfad ist einfach eine Datei oder einen Registrierungsschlüssel Schlüssel, der die gesamte Komponente darstellt.  
  
#### Komponentenanbieter Aufgaben  
  
-   Zwei Ressourcen, die separat in nachfolgenden Versionen enthalten möglicherweise sollte in separate Komponenten vorhanden sein. Ressourcen werden in der gleichen Komponente gruppiert werden, nur, wenn Sie sicher sind, dass diese Ressourcen getrennt nie ausgeliefert werden. Es wird daher empfohlen, alle primären Ressourcen \(z. B. DLLs\) in separaten WICs immer vorhanden sein. Weitere Informationen finden Sie unter [Installationsprogrammkomponenten definieren](http://msdn.microsoft.com/library/aa368269\(VS.85\).aspx).  
  
-   Keine Versionsangabe Ressource sollte jemals mehrere WIC ausgeliefert.  
  
## Siehe auch  
 [Was geschieht, wenn die Komponentenregeln unterbrochen werden?](http://msdn.microsoft.com/library/aa372795\(VS.85\).aspx)