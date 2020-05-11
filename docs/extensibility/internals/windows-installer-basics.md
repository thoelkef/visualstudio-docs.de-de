---
title: Windows Installer-Grundlagen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Windows Installer, VSPackages
- VSPackages, Windows Installer basics
ms.assetid: 497e479b-add8-4644-870a-917f15306b97
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aeea0b17a3c234bb7670642fb9ae0a442c9d60cd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703419"
---
# <a name="windows-installer-basics"></a>Grundlagen zu Windows Installer
Windows Installer installiert und deinstalliert Anwendungen oder Softwareprodukte auf dem Computer eines Benutzers und führt diese Aufgaben in Einheiten aus, die als Windows Installer-Komponenten bezeichnet werden (manchmal auch als WICs oder nur als Komponenten bezeichnet). Eine GUID identifiziert jedes WIC, das die grundlegende Einheit der Installation und Referenzzählung für Setups mit Windows Installer ist.

 Ausführliche Dokumentation des Windows Installerfindens finden Sie im Thema Platform SDK, [Windows Installer](/previous-versions/2kt85ked(v=vs.120)).

## <a name="authoring-a-vspackage"></a>Erstellen eines VSPackage
 Windows Installer verwendet Installationspakete, die Informationen enthalten, die Windows Installer zum Installieren, Deinstallieren oder Reparieren eines Produkts und zum Ausführen der Setup-Benutzeroberfläche (UI) benötigt. Jedes Installationspaket enthält eine MSI-Datei, die eine Installationsdatenbank, einen Zusammenfassungsinformationsstream und Datenströme für verschiedene Teile der Installation enthält. Um das Installationsprogramm verwenden zu können, müssen Sie eine Installation erstellen. Da der Installer Installationen rund um das Konzept der Komponenten organisiert und Informationen über die Installation in einer relationalen Datenbank speichert, umfasst der Prozess der Erstellung eines Installationspakets im Großen und Ganzen die folgenden Schritte:

1. Planen Sie Ihre Setup-Authoring, um Ihre Versions- und Side-by-Side-Strategien zu unterstützen.

2. Identifizieren Sie die Features, die Benutzern präsentiert werden sollen.

3. Organisieren Sie das VSPackage und die Abhängigkeiten in Komponenten.

4. Füllen Sie die Installationsdatenbank mit Informationen aus.

5. Überprüfen Sie das Installationspaket.

   Diese Dokumentation befasst sich in erster Linie mit dem ersten und dritten Schritt des Prozesses. Während dieser Schritte organisieren Sie Ihre VSPackage-Funktionen in WICs, sodass Sie Ihre [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Versions- und Wartungsstrategie so gestalten können, dass sie nachfolgenden Versionen von berücksichtigt. Die verbleibenden drei Schritte werden ausführlich in der Windows Installer-Dokumentation im Platform SDK behandelt.

## <a name="key-terms"></a>Schlüsselbegriffe
 Im Folgenden finden Sie Definitionen von Schlüsselbegriffen, die sich auf die Windows Installer-Technologie beziehen.

 Ressourcendateien, Registrierungsschlüssel, Verknüpfungen usw., die auf einem Computer installiert werden können. Diese Ressourcen werden logisch in Windows Installer-Komponenten gruppiert.

 Windows Installer-Komponente (WIC) Die grundlegende Installationseinheit, die eine logische Gruppierung verwandter Ressourcen darstellt, die als Einheit installiert und deinstalliert werden. Windows Installer-Komponenten werden durch eine eindeutige Komponenten-ID (GUID) identifiziert. Darüber hinaus behält Windows Installer seine Referenzzählung auf WIC-Ebene bei. Für maximale Versionsflexibilität, schließen Sie nicht mehr als eine primäre Ressource, z. B. eine DLL, in einem bestimmten WIC ein. Beachten Sie, dass Sie nach dem Identifizieren und Auffüllen eines WIC eine GUID geben und diese bereitstellen, die Zusammensetzung nicht ändern können. Weitere Informationen finden Sie unter [Organisieren von Anwendungen in Komponenten](/windows/desktop/Msi/organizing-applications-into-components).

 Paket (Redist-Paket) Eine Bereitstellungseinheit, die aus einer MSI-Datei und externen Quelldateien besteht, auf die diese Datei verweisen könnte. Ein Paket enthält alle Informationen, die Windows Installer zum Ausführen der Benutzeroberfläche und zum Installieren oder Deinstallieren der Anwendung benötigt.

 .msi Datei Eine COM-strukturierte Speicherdatei, die die Anweisungen und Daten enthält, die zum Installieren einer Anwendung erforderlich sind. Jedes Paket enthält mindestens eine MSI-Datei. Die MSI-Datei enthält die Installationsdatenbank, einen Zusammenfassungsinformationsstream und möglicherweise eine oder mehrere Transformationen und interne Quelldateien. Die zu installierenden Dateien können entweder in einen Ablageschrank komprimiert und in einem Stream in der MSI-Datei gespeichert oder außerhalb der MSI-Datei auf dem Quellmedium gespeichert, komprimiert oder unkomprimiert gespeichert werden. Weitere Informationen finden Sie unter [Windows Installer File Extensions](/windows/desktop/Msi/windows-installer-file-extensions).

## <a name="windows-installer-rules-enforcement"></a>Windows Installer-Regeln Durchsetzung
 Zwei Regelsätze bestimmen die Bereitstellung von Ressourcen über die Komponenten Ihres Setups. Ein Regelsatz wird vom Windows Installer selbst verwaltet, während Sie den zweiten Satz als Installationsautor erzwingen sollten.

> [!NOTE]
> Die Erzwingung von Windows Installer-Regeln erfolgt nur, wenn Sie eine Überprüfung Ihrer MSI-Datei ausführen. Dennoch werden Sie gewarnt, diese Regeln als bewährte Verfahren zu behandeln. Weitere Informationen finden Sie unter [Überprüfen einer Installationsdatenbank](/windows/desktop/Msi/validating-an-installation-database) und [Paketvalidierung](/windows/desktop/Msi/package-validation).

#### <a name="installer-enforced-rules"></a>Installer-erzwungene Regeln

- Alle Dateien in einer bestimmten Komponente müssen im selben Verzeichnis installiert werden. Umgekehrt müssen Dateien, die in separaten Ordnern installiert sind, zu separaten Komponenten gehören.

- Es kann nur einen Schlüsselpfad pro Komponente geben. Der Schlüsselpfad ist einfach eine Datei oder ein Registrierungsschlüssel, der die gesamte Komponente darstellt.

#### <a name="component-provider-responsibilities"></a>Komponenten-Anbieter-Verantwortlichkeiten

- Zwei ressourcen, die in nachfolgenden Versionen separat geliefert werden können, sollten in separaten Komponenten vorhanden sein. Ressourcen sollten nur dann in derselben Komponente gruppiert werden, wenn Sie sicher sind, dass diese Ressourcen niemals separat versendet werden. Es wird empfohlen, dass alle primären Ressourcen (z. B. DLLs) immer in separaten WICs vorhanden sind. Weitere Informationen finden Sie unter [Definieren von Installerkomponenten](/windows/desktop/Msi/defining-installer-components).

- Keine versionierte Ressource sollte jemals in mehr als einem WIC ausgeliefert werden.

## <a name="see-also"></a>Weitere Informationen
- [Was geschieht, wenn die Komponentenregeln gebrochen sind?](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken)
