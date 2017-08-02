---
title: "VSPackage-Setup-Szenarien | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Aspekte der Bereitstellung von VSPackages"
ms.assetid: d2928498-f27c-46b4-a9cd-cba41fd85a10
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# VSPackage-Setup-Szenarien
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Es ist wichtig, das VSPackage\-Installationsprogramm für Flexibilität zu entwerfen. Beispielsweise müssen Sie möglicherweise einen Sicherheitspatch in Zukunft freigeben oder eine Business\-Strategie, die gründliche Side\-by\-Side\-Unterstützung erfordert unter Umständen ändern.  
  
 In [Unterstützung von mehreren Versionen von Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md), informieren Sie sich über die Vorteile und Probleme bei der Unterstützung von Seite\-an\-Seite\-Installationen von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mit freigegebenen oder Seite\-an\-Seite\-Installationen von Ihr VSPackage. Kurz gesagt, Side\-by\-Side VSPackages bieten Ihnen die größte Flexibilität zur Unterstützung neuer Features von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 In diesem Thema beschriebenen Szenarien sind nicht nur die Optionen, aber empfohlene bewährte Verfahren vorgestellt werden.  
  
## Komponenten, Datenschutz und gemeinsame Nutzung  
  
##### Stellen Sie Ihre Komponenten unabhängig  
 Identifizieren und Auffüllen eine Komponente, weisen eine `GUID`, und stellen Sie die Komponente, die Zusammensetzung kann nicht geändert werden. Wenn Sie eine Komponente Komposition ändern, muss die resultierende Komponente eine neue Komponente mit einem neuen `GUID`. Angesichts dieser Fakten, ist die größte Flexibilität für die Versionskontrolle geboten, und jede Komponente unabhängige, Dank der Einheit. Weitere Informationen zu Regeln für die Komponenten, finden Sie unter [ändern den Code für die Komponente](http://msdn.microsoft.com/library/aa367849\(VS.85\).aspx) und [Was geschieht, wenn die Komponente Regeln werden aufgeteilt?](http://msdn.microsoft.com/library/aa372795\(VS.85\).aspx).  
  
##### Mischen Sie freigegebene und private Ressourcen innerhalb einer Komponente keine  
 Referenzzähler erfolgt auf der Komponentenebene. Folglich wird Mischen von freigegebenen und privaten Ressourcen in einer bestimmten Komponente unmöglich, private Ressourcen, z. B. eine ausführbare Datei zu aktualisieren, ohne freigegebene Ressourcen auch überschreiben. Dieses Szenario erstellt der Abwärtskompatibilität Probleme und verhindert, dass Sie Side\-by\-Side\-Funktion erstellen.  
  
 Z. B. Registrierungswerte zum Registrieren von Ihrem VSPackages mit der [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] bleiben sollen in einer Komponente von einem zum Registrieren Ihrer VSPackages mit separaten [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Freigegebene Dateien oder Registrierungswerte gehen noch eine andere Komponente.  
  
## Szenario 1: Freigegebene VSPackage  
 In diesem Szenario wird ein freigegebener VSPackage \(eine einzelne Binärdatei, die mehrere Versionen von unterstützt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]\) ist im Lieferumfang von Windows Installer\-Paket. Registrieren mit jeder Version von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wird gesteuert, indem auswählbaren Features. Es bedeutet auch, dass wenn zugewiesen, um Funktionen zu trennen, jede Komponente für die Installation oder Deinstallation, dass der Benutzer im Steuerelement VSPackage in verschiedenen Versionen von integrieren kann einzeln ausgewählt werden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. \(Siehe [Features von Windows Installer](http://msdn.microsoft.com/library/aa372840\(VS.85\).aspx) Weitere Informationen zur Verwendung von Funktionen in Windows Installer\-Pakete.\)  
  
 ![Grafik zu freigegebenem VS&#45;Paket](~/extensibility/internals/media/vs_sharedpackage.gif "VS\_SharedPackage")  
Freigegebene VSPackage\-installer  
  
 Wie in der Abbildung gezeigt, erfolgen gemeinsam genutzte Komponenten Teil der Feat\_Common\-Funktion, die immer installiert wird. Sichtbarmachen der Feat\_VS2002 und Feat\_VS2003 Funktionen, Benutzer können auswählen, zum Zeitpunkt der Installation in die Versionen von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage integrieren wollen. Benutzer können auch Windows Installer\-Wartungsmodus hinzufügen oder Entfernen von Features, die in diesem Fall fügt hinzu oder entfernt die Registrierungsinformationen VSPackage aus verschiedenen Versionen der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
> [!NOTE]
>  Ein Feature Anzeigespalte auf 0 festlegen ausgeblendet. Ein Spalte mit niedrigen Ebene\-Wert, z. B. 1, wird sichergestellt, dass es immer installiert wird. Weitere Informationen finden Sie unter [INSTALLLEVEL Eigenschaft](http://msdn.microsoft.com/library/aa369536\(VS.85\).aspx) und [Funktionstabelle](http://msdn.microsoft.com/library/aa368585.aspx).  
  
## Szenario 2: Freigegebene VSPackage\-Update  
 In diesem Szenario wird eine aktualisierte Version des Installationsprogramms VSPackage in Szenario 1 geliefert. Im Rahmen dieser Erörterung, das Update fügt Unterstützung für [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], aber es könnte auch ein einfacher Security Patch oder die Fehlerkorrektur Servicepack. Windows Installer Regeln für die Installation neuer Komponenten müssen unveränderte Komponenten bereits auf dem System nicht kopiert werden. In diesem Fall ein System mit Version 1.0 bereits aktualisierte Komponente Comp\_MyVSPackage.dll überschreibt und ermöglicht Benutzern das neue Feature Feat\_VS2005 mit seiner Komponente Comp\_VS2005\_Reg hinzufügen.  
  
> [!CAUTION]
>  Ein VSPackage ist jedes Mal, wenn mehrere Versionen freigegeben [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], ist es wichtig, dass die nachfolgende Versionen des VSPackage Abwärtskompatibilität mit früheren Versionen von beibehalten [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Bei der Abwärtskompatibilität beibehalten werden kann, müssen Sie die Seite\-an\-Seite, private VSPackages verwenden. Weitere Informationen finden Sie unter [Unterstützung von mehreren Versionen von Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).  
  
 ![Bild zur Aktualisierung von freigegebenem VS&#45;Paket](~/extensibility/internals/media/vs_sharedpackageupdate.gif "VS\_SharedPackageUpdate")  
Freigegebene VSPackage\-Updateinstallationsprogramm  
  
 Dieses Szenario stellt einen neuen VSPackage\-Installer, Windows Installer Unterstützung für kleineren Updates zu nutzen. Benutzer einfach installieren Sie Version 1.1 und Version 1.0 Upgrade. Es ist jedoch nicht notwendig, damit auf dem System, Version 1.0. Das gleiche Installationsprogramm installiert Version 1.1 auf einem System ohne Version 1.0. Der Vorteil bei der kleinen Upgrades auf diese Weise ist, dass es nicht notwendig, die Arbeit der Entwicklung einer Aktualisierung Installationsprogramm und eine Vollversion durchlaufen. Ein Installationsprogramm führt beide Aufträge. Ein Sicherheitsupdate oder ein Service pack möglicherweise stattdessen Windows Installer\-Patches zu nutzen. Weitere Informationen finden Sie unter [Patchen und Upgrades](http://msdn.microsoft.com/library/aa370579\(VS.85\).aspx).  
  
## Szenario 3: Side\-by\-Side VSPackage  
 Dieses Szenario zeigt zwei VSPackage\-Installationsprogramme – eine für jede Version von Visual Studio .NET 2003 und [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Jedes Installationsprogramm installiert eine Seite\-an\-Seite oder Private VSPackage \(eines, das speziell für eine bestimmte Version eines installierten [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]\). Jede VSPackage ist in der eigenen Komponente. Aus diesem Grund jede kann einzeln verwaltet werden mit Patches oder Wartung frei. Da VSPackage\-DLL nun Version ist, ist es sicher ist, die zugehörigen Registrierungsinformationen in der gleichen Komponente wie die DLL enthalten.  
  
 ![Grafik zu parallelem VS&#45;Paket](~/extensibility/internals/media/vs_sbys_package.gif "VS\_SbyS\_Package")  
Side\-by\-Side VSPackage\-installer  
  
 Jedes Installationsprogramm enthält auch Code, der die zwei Installer gemeinsam verwendet wird. Wenn der freigegebene Code an einem Standort installiert ist, installiert installieren beide MSI\-Dateien den gemeinsam verwendeten Code nur einmal. Der zweite Installer erhöht nur einen Verweiszähler für die Komponente. Der Verweiszähler wird sichergestellt, wenn eines der VSPackages deinstalliert wird, der Code gemeinsame für die anderen VSPackage bleiben. Wenn das zweite VSPackage ebenfalls deinstalliert wird, werden die freigegebene Code entfernt.  
  
## Szenario 4: Side\-by\-Side VSPackage\-Update  
 In diesem Szenario wird das VSPackage für [!INCLUDE[vsprvslong](../../code-quality/includes/vsprvslong_md.md)] erlitten Sicherheit Schwachstelle und Sie müssen ein Update. Wie in Szenario 2 können Sie eine neue MSI\-Datei erstellen, die eine vorhandene Installation aktualisiert, um das Sicherheitsupdate enthalten sowie das Bereitstellen neuer Installationen mit dem Sicherheitsupdate bereits vorhanden.  
  
 In diesem Fall ist das VSPackage verwaltete VSPackages im globalen Assemblycache \(GAC\) installiert. Wenn Sie damit die Sicherheit bieten neu erstellen, müssen Sie die Revision der Dateiteil mit der Versionsnummer der Assembly ändern. Die Registrierungsinformationen für die neue Versionsnummer der Assembly auf die vorherige Version überschreibt, wodurch [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zum Laden der Assembly festen.  
  
 ![Grafik zur Aktualisierung von parallelem VS&#45;Paket](~/extensibility/internals/media/vs_sbys_packageupdate.gif "VS\_SbyS\_PackageUpdate")  
Side\-by\-Side VSPackage\-Updateinstallationsprogramm  
  
 **Hinweis** Weitere Informationen zur Bereitstellung von Side\-by\-Side\-Assemblys finden Sie unter [Bereitstellung vereinfachen und Beheben von DLL\-Hölle mit .NET Framework](http://msdn.microsoft.com/library/ms973843.aspx).  
  
## Siehe auch  
 [Windows Installer](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [Unterstützung von mehreren Versionen von Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)