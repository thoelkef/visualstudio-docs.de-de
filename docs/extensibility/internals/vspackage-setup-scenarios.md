---
title: VSPackage-Setupszenarien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, deployment considerations
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a3dfe3f3c135cb3ed16c7550fc62d334cc548cd1
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2018
ms.locfileid: "39510665"
---
# <a name="vspackage-setup-scenarios"></a>VSPackage-Setupszenarien

Es ist wichtig, um Ihre VSPackage-Installationsprogramm für Flexibilität zu entwerfen. Beispielsweise müssen Sie möglicherweise einen Sicherheitspatch in der Zukunft freigeben oder Business-Strategien, die eingehende Seite-an-Seite-versionsunterstützung erfordert unter Umständen ändern.

In [unterstützt mehrere Versionen von Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md), informieren Sie sich über die Vorteile und Probleme für die Unterstützung von Seite-an-Seite-Installationen von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mit entweder freigegeben oder Seite-an-Seite-Installationen von Ihres VSPackage. Kurz gesagt, VSPackages von Seite-an-Seite bieten Ihnen die größte Flexibilität zur Unterstützung neuer Funktionen von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

Die in diesem Thema behandelten Szenarien sind nicht Ihre einzigen Möglichkeiten, aber sie werden als Vorschläge zu bewährten Methoden dargestellt.

## <a name="components-privacy-and-sharing"></a>Komponenten, Datenschutz und Freigabe

### <a name="make-your-components-independent"></a>Stellen Sie Ihre Komponenten unabhängig

Nachdem Sie identifizieren, und füllen Sie eine Komponente, weisen eine `GUID`, und stellen Sie die Komponente, die Zusammensetzung kann nicht geändert werden. Wenn Sie einer Komponente Komposition ändern, muss die resultierende Komponente eine neue Komponente mit einem neuen `GUID`. Wenn diese Fakten, ist die größte Flexibilität für die versionsverwaltung verfügbaren machen jede Komponente unabhängig, selbständig einen detaillierten Einheit. Weitere Informationen zu Regeln für die Komponenten, finden Sie unter [Ändern des Codes für die Komponente](/windows/desktop/Msi/changing-the-component-code) und [was geschieht, wenn die Komponente Regeln werden unterteilt?](http://msdn.microsoft.com/library/aa372795\(VS.85\).aspx).

### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>Mischen Sie freigegebene und private Ressourcen in eine Komponente nicht

Verweiszählung tritt auf, auf der Komponentenebene. Daher macht freigegebene und private Ressourcen in einer Komponente Mischung es unmöglich, private Ressourcen, z. B. eine ausführbare Datei, zu aktualisieren, ohne auch Überschreiben von freigegebenen Ressourcen. Dieses Szenario Abwärtskompatibilität Probleme erstellt, und Sie darauf beschränkt, von der Erstellung von Seite-an-Seite-Funktion.

Z. B. Registrierungswerte zum Registrieren von VSPackage mit der [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] beibehalten werden sollen in einer Komponente getrennt von einem verwendet, um Ihr VSPackage in Visual Studio zu registrieren. Freigegebene Dateien oder Registrierungseinträge können im noch eine andere Komponente.

## <a name="scenario-1-shared-vspackage"></a>Szenario 1: Freigegebene VSPackage

In diesem Szenario wird ein freigegebener VSPackage (eine einzelne Binärdatei, die mehrere Versionen von Visual Studio unterstützt wird in ein Windows Installer-Paket versendet. Mit jeder Version von Visual Studio registrieren, wird von auswählbaren Features gesteuert. Es bedeutet auch, dass wenn zugewiesen, um Funktionen zu trennen, jede Komponente für die Installation oder Deinstallation, platzieren den Benutzer Kontrolle über das VSPackage in verschiedenen Versionen von integrieren kann einzeln ausgewählt werden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. (Finden Sie unter [Features von Windows Installer](/windows/desktop/Msi/windows-installer-features) für Weitere Informationen zur Verwendung von Features in Windows Installer-Pakete.)

![Freigegebenem VS-Installer](../../extensibility/internals/media/vs_sharedpackage.gif "VS_SharedPackage")

Wie in der Abbildung gezeigt wird, werden freigegebene Komponenten Teil des Features Feat_Common durchgeführt, das immer installiert sind. Indem Sie die Feat_VS2002 und Feat_VS2003 Features sichtbar machen, können Benutzer zum Zeitpunkt der Installation wählen, in welche Versionen von Visual Studio sie das VSPackage, um integrieren möchten. Benutzer können auch Windows Installer-Wartungsmodus hinzufügen oder Entfernen von Funktionen, die in diesem Fall fügt hinzu oder entfernt die VSPackage-Registrierungsinformationen aus verschiedenen Versionen von Visual Studio.

> [!NOTE]
> Ein Feature der Anzeigespalte auf 0 festlegen, blendet ihn aus. Ein niedrige Ebene Spaltenwert, z. B. 1, wird sichergestellt, dass es immer installiert wird. Weitere Informationen finden Sie unter [INSTALLLEVEL Eigenschaft](/windows/desktop/Msi/installlevel) und [Funktionstabelle](/windows/desktop/Msi/feature-table).

## <a name="scenario-2-shared-vspackage-update"></a>Szenario 2: Freigegebene VSPackage-Update

In diesem Szenario wird eine aktualisierte Version des VSPackage-Installationsprogramms in Szenario 1 ausgeliefert. Aus Gründen der Erläuterung das Update bietet Unterstützung für Visual Studio, aber es kann auch ein einfacher Sicherheitspatch oder Fehlerkorrektur Servicepacks. Windows Installer Regeln für die Installation neuer Komponenten müssen unveränderte Komponenten bereits auf dem System nicht erneut kopiert werden. In diesem Fall wird die aktualisierte Komponente Comp_MyVSPackage.dll ein System mit Version 1.0, die bereits vorhandenen überschrieben und können Benutzer das neue Feature Feat_VS2005 mit seiner Komponente Comp_VS2005_Reg hinzufügen.

> [!CAUTION]
> Eine VSPackage wird jedes Mal, wenn mehrere Versionen freigegeben [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], es ist wichtig, dass es sich bei nachfolgende Versionen des VSPackage Abwärtskompatibilität mit früheren Versionen von Visual Studio zu gewährleisten. Wenn Sie Abwärtskompatibilität aufrechtzuerhalten, müssen Sie die Seite-an-Seite, private VSPackages verwenden. Weitere Informationen finden Sie unter [unterstützt mehrere Versionen von Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).

![VS-Paketupdate für freigegebene Visual Studio-Installer](../../extensibility/internals/media/vs_sharedpackageupdate.gif "VS_SharedPackageUpdate")

Dieses Szenario stellt einen neuen VSPackage-Installer, Windows Installer Unterstützung für nebensächliche Upgrades zu nutzen. Benutzer einfach installieren Sie Version 1.1, und es wird Version 1.0 aktualisiert. Allerdings ist es nicht notwendig, Version 1.0 auf dem System haben. Der gleiche Installer wird Version 1.1 auf einem System ohne Version 1.0 installieren. Der Vorteil, geben Sie kleiner Upgrades auf diese Weise ist, dass es nicht notwendig, die Arbeit der Entwicklung ein Installationsprogramm für Upgrades und ein Installationsprogramm Bruders durchlaufen. Ein Installationsprogramm führt beide Aufträge. Eine Sicherheitsupdates oder die Service pack möglicherweise stattdessen Windows Installer-Patches zu nutzen. Weitere Informationen finden Sie unter [Patchen und Upgrades](/windows/desktop/Msi/patching-and-upgrades).

## <a name="scenario-3-side-by-side-vspackage"></a>Szenario 3: Seite-an-Seite-VSPackage

Dieses Szenario zeigt zwei Installationsprogramme für VSPackage – eine für jede Version von Visual Studio .NET 2003 und Visual Studio. Jedes Installationsprogramm installiert eine Seite-an-Seite oder "Private", "VSPackage (diejenige, die explizit erstellt und für eine bestimmte Version von Visual Studio installiert wird). Jedes VSPackage wird in eine eigene Komponente. Daher jede kann einzeln gewartet werden mit Patches oder Wartung frei. Da die VSPackage-DLL nun hängt von der Version ist, ist es sicher ist, die Registrierungsinformationen in der gleichen Komponente wie die DLL enthalten.

![Visual Studio-Seite-an-Seite-VS-Paket-Installer](../../extensibility/internals/media/vs_sbys_package.gif "VS_SbyS_Package")

Jedes Installationsprogramm enthält auch Code, der die zwei Installer gemeinsam verwendet wird. Wenn der freigegebene Code an einem Standort installiert ist, werden beide MSI-Dateien den freigegebenen Code nur einmal installieren. Das zweite Installationsprogramm erhöht nur einen Verweiszähler für die Komponente. Der Verweiszähler wird sichergestellt, dass wenn eines der VSPackages deinstalliert wird, der freigegebene Code für die anderen VSPackage bleibt. Wenn das zweite VSPackage ebenfalls deinstalliert wird, wird der freigegebene Code entfernt.

## <a name="scenario-4-side-by-side-vspackage-update"></a>Szenario 4: Seite-an-Seite VSPackage-Update

In diesem Szenario das VSPackage für Visual Studio aus eine Sicherheitslücke ist, und müssen Sie ein Update. Wie in Szenario 2 können Sie eine neue MSI-Datei erstellen, die aktualisiert eine vorhandene Installation aus, um die Lösung für Sicherheit, sowie Bereitstellen von neuen Installationen mit der Sicherheit Behebung bereits vorhanden.

In diesem Fall ist das VSPackage ein verwaltetes VSPackage, die im globalen Assemblycache (GAC) installiert. Wenn Sie damit die Sicherheit Korrektur neu erstellen, müssen Sie die Revision Number Teil der Versionsnummer der Assembly ändern. Die Registrierungsinformationen für die neue Versionsnummer der Assembly auf die vorherige Version überschreiben, wodurch [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zum Laden der Assembly festen.

![VS Update Seite-an-Seite der Visual Studio-Installer](../../extensibility/internals/media/vs_sbys_packageupdate.gif "VS_SbyS_PackageUpdate")

Weitere Informationen zur Bereitstellung von Seite-an-Seite-Assemblys finden Sie unter [Bereitstellung vereinfachen und Beheben von DLL-Hölle mit .NET Framework](http://msdn.microsoft.com/library/ms973843.aspx).

## <a name="see-also"></a>Siehe auch

[Windows Installer](/windows/desktop/Msi/windows-installer-portal)  
[Unterstützen mehrerer Versionen von Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)