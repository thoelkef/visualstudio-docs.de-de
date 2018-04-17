---
title: Windows Installer-Grundlagen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Windows Installer, VSPackages
- VSPackages, Windows Installer basics
ms.assetid: 497e479b-add8-4644-870a-917f15306b97
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8fba35aba1e1947ee4eeeb59ca2225253e2aa3a8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="windows-installer-basics"></a>Grundlagen von Windows Installer
Windows Installer installiert und deinstalliert, Anwendungen oder Softwareprodukte auf dem Computer eines Benutzers, das Ausführen dieser Aufgaben in so genannten Windows Installer-Komponenten (manchmal auch als WICs oder nur Komponenten bezeichnet). Eine GUID identifiziert jede WIC, die die grundlegende Einheit von Installations- und verweiszählung für Installationen mit Windows Installer ist.  
  
 Eine umfassende Dokumentation der Windows Installer finden Sie in der Platform SDK unter [Windows Installer](http://msdn.microsoft.com/library/aa372866.aspx).  
  
## <a name="authoring-a-vspackage"></a>Erstellen eine VSPackage  
 Windows Installer verwendet Installationspakete, die Informationen, die Windows Installer enthalten zu installieren, deinstallieren oder reparieren ein Produkts und der Setup-Benutzeroberfläche (UI) auszuführen. Jedem Installationspaket enthält eine MSI-Datei, die eine Installationsdatenbank, einen Stream zusammenfassende Informationen und Datenströme für verschiedene Teile der Installation enthält. Um das Installationsprogramm zu verwenden, müssen Sie eine Installation erstellen. Da vom Installer Installationen auf dem Konzept von Komponenten organisiert und Informationen zur Installation in einer relationalen Datenbank gespeichert, umfasst der Prozess erstellen ein Installationspaket Allgemein die folgenden Schritte aus:  
  
1.  Planen Sie Ihrer Einrichtung, die zur Unterstützung der versionsverwaltung und Strategien für Seite-an-Seite erstellen.  
  
2.  Identifizieren Sie die Funktionen, die den Benutzern angezeigt werden.  
  
3.  Organisieren Sie das VSPackage und Abhängigkeiten in Komponenten an.  
  
4.  Füllen Sie die Installationsdatenbank mit Informationen.  
  
5.  Überprüfen Sie das Installationspaket ein.  
  
 Diese Dokumentation ist in erster Linie mit der ersten und dritten Schritte des Prozesses besorgt. Beim Ausführen dieser Schritte Sie Ihr VSPackage-Funktionen in organisieren WICs, damit Sie Ihre versionsverwaltung und Wartung der Strategie für die nachfolgenden Versionen des Konto frame können [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Die verbleibenden drei Schritte sind in der Windows Installer-Dokumentation in der Platform SDK detailliert beschrieben.  
  
## <a name="key-terms"></a>Schlüsselbegriffe  
 Es folgen Definitionen wichtiger Begriffe im Zusammenhang mit der Windows Installer-Technologie.  
  
 Ressource  
 Dateien, Registrierungsschlüsseln, die Tastenkombinationen, oder usw., die auf einem Computer installiert werden kann. Diese Ressourcen werden in Windows Installer-Komponenten logisch gruppiert.  
  
 Windows Installer-Komponente (WIC)  
 Die grundlegende Einheit der Installation, die eine logische Gruppierung von verwandten Ressourcen, die installiert und deinstalliert werden, als eine Einheit darstellt. Windows Installer-Komponenten werden durch eine eindeutige Komponenten-ID oder GUID identifiziert. Windows Installer verwaltet außerdem die verweiszählung Ebene WIC. Versionsverwaltung maximale Flexibilität erhalten Sie schließen Sie nicht mehr als eine primäre Ressource, z. B. eine DLL in einer bestimmten WIC aus. Beachten Sie, dass Sie nach dem identifizieren und eine WIC aufzufüllen, geben Sie ihm eine GUID und bereitstellen, die Zusammensetzung ändern können. Weitere Informationen finden Sie unter [Organisieren von Anwendungen in Komponenten](http://msdn.microsoft.com/library/aa370561.aspx).  
  
 Paket (Redist-Paket)  
 Eine Einheit der Bereitstellung, die besteht aus einer MSI-Datei und externen Quelldateien auf denen diese Datei verweisen kann. Ein Paket enthält alle Informationen, die Windows Installer muss die Benutzeroberfläche ausführen und das Installieren oder Deinstallieren der Anwendung.  
  
 MSI-Datei  
 Eine COM-strukturierte-Speicherdatei, die die Anweisungen und die Installation eine Anwendung erforderlichen Daten enthält. Jedes Paket enthält mindestens eine MSI-Datei. Die MSI-Datei enthält das Installer-Datenbank, einen Stream zusammenfassende Informationen und möglicherweise eine oder mehrere Transformationen und interne Quelldateien. Zu installierenden Dateien können entweder in eine CAB-Datei komprimiert und in einen Stream in der MSI-Datei gespeichert oder gespeichert, komprimiert oder dekomprimiert, außerhalb der MSI-Datei auf das Quellmedium. Weitere Informationen finden Sie unter [Windows Installer-Dateierweiterungen](http://msdn.microsoft.com/library/aa372842\(VS.85\).aspx).  
  
## <a name="windows-installer-rules-enforcement"></a>Windows Installer-Regeln erzwungen  
 Zwei Sätze von Regeln bestimmen die Bereitstellung von Ressourcen über die Setup-Komponenten. Ein Regelsatz wird vom Windows Installer selbst beibehalten, während Sie auf der zweiten Menge als Autor Installation erzwingen soll.  
  
> [!NOTE]
>  Durchsetzung von Windows Installer-Regeln tritt nur dann, wenn Sie eine Überprüfung der MSI-Datei ausführen. Trotzdem sind Sie cautioned, diese Regeln als bewährte Methoden zu behandeln. Weitere Informationen finden Sie unter [Überprüfen einer Installationsdatenbank](http://msdn.microsoft.com/library/aa372477\(VS.85\).aspx) und [Paketüberprüfung](http://msdn.microsoft.com/library/aa370569\(VS.85\).aspx).  
  
#### <a name="installer-enforced-rules"></a>Erzwungene Installer-Regeln  
  
-   Alle Dateien in einer bestimmten Komponente müssen in dasselbe Verzeichnis installiert werden. Im Gegensatz dazu müssen Dateien in separaten Ordnern installiert gehören, um Komponenten zu trennen.  
  
-   Es kann nur ein Schlüsselpfad pro Komponente vorhanden sein. Der Schlüsselpfad ist einfach eine Datei oder ein Registrierungsschlüsselwert Schlüssel, der die gesamte Komponente darstellt.  
  
#### <a name="component-provider-responsibilities"></a>Komponentenanbieter Aufgaben  
  
-   Alle zwei Ressourcen, die in zukünftigen Versionen separat liefern können, sollten in separaten Komponenten vorhanden sein. Ressourcen sollten in der gleichen Komponente gruppiert werden, nur, wenn Sie sicher sind, dass diese Ressourcen getrennt nie ausgeliefert werden. Es ist in der Tat empfohlen, dass alle primären Ressourcen (z. B. DLLs) in separaten WICs immer vorhanden. Weitere Informationen finden Sie unter [Installationsprogrammkomponenten definieren](http://msdn.microsoft.com/library/aa368269\(VS.85\).aspx).  
  
-   Keine mit Versionsangabe Ressource sollte jemals in mehr als eine WIC liefern.  
  
## <a name="see-also"></a>Siehe auch  
 [Was geschieht, wenn die Komponentenregeln unterbrochen werden?](http://msdn.microsoft.com/library/aa372795\(VS.85\).aspx)