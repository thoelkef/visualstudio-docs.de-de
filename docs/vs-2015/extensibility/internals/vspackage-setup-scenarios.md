---
title: VSPackage-Setupszenarien | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, deployment considerations
ms.assetid: d2928498-f27c-46b4-a9cd-cba41fd85a10
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 58b4350812900bc11e8aaa3222b3b0898db19e13
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440787"
---
# <a name="vspackage-setup-scenarios"></a>VSPackage-Setupszenarien
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Es ist wichtig, um Ihre VSPackage-Installationsprogramm für Flexibilität zu entwerfen. Beispielsweise müssen Sie möglicherweise einen Sicherheitspatch in der Zukunft freigeben oder Business-Strategien, die eingehende Seite-an-Seite-versionsunterstützung erfordert unter Umständen ändern.  
  
 In [unterstützt mehrere Versionen von Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md), informieren Sie sich über die Vorteile und Probleme für die Unterstützung von Seite-an-Seite-Installationen von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] mit entweder freigegeben oder Seite-an-Seite-Installationen von Ihres VSPackage. Kurz gesagt, VSPackages von Seite-an-Seite bieten Ihnen die größte Flexibilität zur Unterstützung neuer Funktionen von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 Die in diesem Thema behandelten Szenarien sind nicht Ihre einzigen Möglichkeiten, aber sie werden als Vorschläge zu bewährten Methoden dargestellt.  
  
## <a name="components-privacy-and-sharing"></a>Komponenten, Datenschutz und Freigabe  
  
##### <a name="make-your-components-independent"></a>Stellen Sie Ihre Komponenten unabhängig  
 Nachdem Sie identifizieren, und füllen Sie eine Komponente, weisen eine `GUID`, und stellen Sie die Komponente, die Zusammensetzung kann nicht geändert werden. Wenn Sie einer Komponente Komposition ändern, muss die resultierende Komponente eine neue Komponente mit einem neuen `GUID`. Wenn diese Fakten, ist die größte Flexibilität für die versionsverwaltung verfügbaren machen jede Komponente unabhängig, selbständig einen detaillierten Einheit. Weitere Informationen zu Regeln für die Komponenten, finden Sie unter [Ändern des Codes für die Komponente](http://msdn.microsoft.com/library/aa367849\(VS.85\).aspx) und [was geschieht, wenn die Komponente Regeln werden unterteilt?](http://msdn.microsoft.com/library/aa372795\(VS.85\).aspx).  
  
##### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>Mischen Sie freigegebene und private Ressourcen in eine Komponente nicht  
 Verweiszählung tritt auf, auf der Komponentenebene. Daher macht freigegebene und private Ressourcen in einer Komponente Mischung es unmöglich, private Ressourcen, z. B. eine ausführbare Datei, zu aktualisieren, ohne auch Überschreiben von freigegebenen Ressourcen. Dieses Szenario Abwärtskompatibilität Probleme erstellt, und Sie darauf beschränkt, von der Erstellung von Seite-an-Seite-Funktion.  
  
 Z. B. Registrierungswerte zum Registrieren von VSPackage mit der [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] beibehalten werden sollen in einer Komponente von einem zum Registrieren von VSPackage mit separaten [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Freigegebene Dateien oder Registrierungseinträge können im noch eine andere Komponente.  
  
## <a name="scenario-1-shared-vspackage"></a>Szenario 1: Freigegebene VSPackage  
 In diesem Szenario wird ein freigegebener VSPackage (eine einzelne Binärdatei, die mehrere Versionen unterstützt [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]) wird in einem Windows Installer-Paket ausgeliefert. Registrieren mit jeder Version von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] von auswählbaren Features gesteuert wird. Es bedeutet auch, dass wenn zugewiesen, um Funktionen zu trennen, jede Komponente für die Installation oder Deinstallation, platzieren den Benutzer Kontrolle über das VSPackage in verschiedenen Versionen von integrieren kann einzeln ausgewählt werden [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. (Finden Sie unter [Features von Windows Installer](http://msdn.microsoft.com/library/aa372840\(VS.85\).aspx) für Weitere Informationen zur Verwendung von Features in Windows Installer-Pakete.)  
  
 ![Grafik zu freigegebenem VS](../../extensibility/internals/media/vs-sharedpackage.gif "VS_SharedPackage")  
Freigegebene VSPackage-installer  
  
 Wie in der Abbildung gezeigt wird, werden freigegebene Komponenten Teil des Features Feat_Common durchgeführt, das immer installiert sind. Benutzer können, indem Sie die Feat_VS2002 und Feat_VS2003 Features sichtbar machen, zum Zeitpunkt der Installation in die Versionen der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] wollen, dass das VSPackage, um zu integrieren. Benutzer können auch Windows Installer-Wartungsmodus hinzufügen oder Entfernen von Funktionen, die in diesem Fall fügt hinzu oder entfernt die VSPackage-Registrierungsinformationen aus verschiedenen Versionen der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
> [!NOTE]
> Ein Feature der Anzeigespalte auf 0 festlegen, blendet ihn aus. Ein niedrige Ebene Spaltenwert, z. B. 1, wird sichergestellt, dass es immer installiert wird. Weitere Informationen finden Sie unter [INSTALLLEVEL Eigenschaft](http://msdn.microsoft.com/library/aa369536\(VS.85\).aspx) und [Funktionstabelle](http://msdn.microsoft.com/library/aa368585.aspx).  
  
## <a name="scenario-2-shared-vspackage-update"></a>Szenario 2: Freigegebene VSPackage-Update  
 In diesem Szenario wird eine aktualisierte Version des VSPackage-Installationsprogramms in Szenario 1 ausgeliefert. Aus Gründen der Erläuterung, das Update bietet Unterstützung für [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], es kann jedoch auch ein einfacher Security Patch oder die Fehlerkorrektur Servicepack. Windows Installer Regeln für die Installation neuer Komponenten müssen unveränderte Komponenten bereits auf dem System nicht erneut kopiert werden. In diesem Fall wird die aktualisierte Komponente Comp_MyVSPackage.dll ein System mit Version 1.0, die bereits vorhandenen überschrieben und können Benutzer das neue Feature Feat_VS2005 mit seiner Komponente Comp_VS2005_Reg hinzufügen.  
  
> [!CAUTION]
> Eine VSPackage wird jedes Mal, wenn mehrere Versionen freigegeben [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], es ist wichtig, dass es sich bei nachfolgende Versionen des VSPackage mit früheren Versionen der Abwärtskompatibilität [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Wenn Sie Abwärtskompatibilität aufrechtzuerhalten, müssen Sie die Seite-an-Seite, private VSPackages verwenden. Weitere Informationen finden Sie unter [unterstützt mehrere Versionen von Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).  
  
 ![Von freigegebenem VS-Paket aktualisieren Abbilds](../../extensibility/internals/media/vs-sharedpackageupdate.gif "VS_SharedPackageUpdate")  
VSPackage-Updateinstallationsprogramm freigegeben  
  
 Dieses Szenario stellt einen neuen VSPackage-Installer, Windows Installer Unterstützung für nebensächliche Upgrades zu nutzen. Benutzer einfach installieren Sie Version 1.1, und es wird Version 1.0 aktualisiert. Allerdings ist es nicht notwendig, Version 1.0 auf dem System haben. Der gleiche Installer wird Version 1.1 auf einem System ohne Version 1.0 installieren. Der Vorteil, geben Sie kleiner Upgrades auf diese Weise ist, dass es nicht notwendig, die Arbeit der Entwicklung ein Installationsprogramm für Upgrades und ein Installationsprogramm Bruders durchlaufen. Ein Installationsprogramm führt beide Aufträge. Eine Sicherheitsupdates oder die Service pack möglicherweise stattdessen Windows Installer-Patches zu nutzen. Weitere Informationen finden Sie unter [Patchen und Upgrades](http://msdn.microsoft.com/library/aa370579\(VS.85\).aspx).  
  
## <a name="scenario-3-side-by-side-vspackage"></a>Szenario 3: Seite-an-Seite-VSPackage  
 Dieses Szenario zeigt zwei Installationsprogramme für VSPackage – eine für jede Version von Visual Studio .NET 2003 und [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Jedes Installationsprogramm installiert wird, eine Seite-an-Seite oder "Private", "VSPackage (eine, die speziell erstellt und für eine bestimmte Version von installiert [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]). Jedes VSPackage wird in eine eigene Komponente. Daher jede kann einzeln gewartet werden mit Patches oder Wartung frei. Da die VSPackage-DLL nun hängt von der Version ist, ist es sicher ist, die Registrierungsinformationen in der gleichen Komponente wie die DLL enthalten.  
  
 ![Visual Studio-Seite&#45;von&#45;Seite Visual Studio-Pakets zu](../../extensibility/internals/media/vs-sbys-package.gif "VS_SbyS_Package")  
Seite-an-Seite VSPackage-installer  
  
 Jedes Installationsprogramm enthält auch Code, der die zwei Installer gemeinsam verwendet wird. Wenn der freigegebene Code an einem Standort installiert ist, werden beide MSI-Dateien den freigegebenen Code nur einmal installieren. Das zweite Installationsprogramm erhöht nur einen Verweiszähler für die Komponente. Der Verweiszähler wird sichergestellt, dass wenn eines der VSPackages deinstalliert wird, der freigegebene Code für die anderen VSPackage bleibt. Wenn das zweite VSPackage ebenfalls deinstalliert wird, wird der freigegebene Code entfernt.  
  
## <a name="scenario-4-side-by-side-vspackage-update"></a>Szenario 4: Seite-an-Seite VSPackage-Update  
 In diesem Szenario, das VSPackage für [!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)] ist Sicherheit Sicherheitsrisiko und Sie müssen ein Update ausgeben. Wie in Szenario 2 können Sie eine neue MSI-Datei erstellen, die aktualisiert eine vorhandene Installation aus, um die Lösung für Sicherheit, sowie Bereitstellen von neuen Installationen mit der Sicherheit Behebung bereits vorhanden.  
  
 In diesem Fall ist das VSPackage ein verwaltetes VSPackage, die im globalen Assemblycache (GAC) installiert. Wenn Sie damit die Sicherheit Korrektur neu erstellen, müssen Sie die Revision Number Teil der Versionsnummer der Assembly ändern. Die Registrierungsinformationen für die neue Versionsnummer der Assembly auf die vorherige Version überschreiben, wodurch [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zum Laden der Assembly festen.  
  
 ![Visual Studio-Seite&#45;von&#45;Seite VS-Paketupdate Grafik](../../extensibility/internals/media/vs-sbys-packageupdate.gif "VS_SbyS_PackageUpdate")  
Seite-an-Seite VSPackage-Updateinstallationsprogramm  
  
 **Beachten Sie** finden Sie weitere Informationen zur Bereitstellung von Seite-an-Seite-Assemblys [Bereitstellung vereinfachen und Beheben von DLL-Hölle mit .NET Framework](http://msdn.microsoft.com/library/ms973843.aspx).  
  
## <a name="see-also"></a>Siehe auch  
 [Windows Installer](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [Unterstützen mehrerer Versionen von Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)
