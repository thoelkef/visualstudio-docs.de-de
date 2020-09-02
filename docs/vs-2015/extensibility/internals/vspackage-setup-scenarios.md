---
title: VSPackage-Setup Szenarien | Microsoft-Dokumentation
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
ms.openlocfilehash: a09b794a6cd81966df45a1b30182040d7ab9335e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696754"
---
# <a name="vspackage-setup-scenarios"></a>VSPackage-Setupszenarien
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Es ist wichtig, dass Sie das VSPackage-Installationsprogramm flexibel gestalten. Beispielsweise müssen Sie möglicherweise in der Zukunft einen Sicherheitspatches veröffentlichen, oder Sie können eine Geschäftsstrategie ändern, die eine gründliche Unterstützung der parallelen Versionsverwaltung erfordert.  
  
 Wenn Sie [mehrere Versionen von Visual Studio unterstützen](../../extensibility/supporting-multiple-versions-of-visual-studio.md), können Sie sich über die Vorteile und Probleme bei der Unterstützung paralleler Installationen von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] mit freigegebenen oder parallelen Installationen Ihres VSPackage informieren. Kurz gesagt bieten Ihnen parallele VSPackages die größte Flexibilität bei der Unterstützung neuer Funktionen von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 Die in diesem Thema erläuterten Szenarien sind nicht Ihre einzige Wahl, sondern werden als empfohlene bewährte Methoden vorgestellt.  
  
## <a name="components-privacy-and-sharing"></a>Komponenten, Datenschutz und Freigabe  
  
##### <a name="make-your-components-independent"></a>Machen Sie Ihre Komponenten unabhängig  
 Nachdem Sie eine Komponente identifiziert und aufgefüllt, eine zugewiesen `GUID` und die Komponente bereitgestellt haben, können Sie deren Komposition nicht mehr ändern. Wenn Sie die Zusammensetzung einer Komponente ändern, muss die resultierende Komponente eine neue Komponente mit einem neuen sein `GUID` . Angesichts dieser Fakten wird die größte Flexibilität bei der Versionsverwaltung erzielt, indem jede Komponente unabhängig voneinander unabhängig voneinander unabhängig gemacht wird. Weitere Informationen zu Regeln, die Komponenten steuern, finden Sie unter [Ändern des Komponenten Codes](https://msdn.microsoft.com/library/aa367849\(VS.85\).aspx) und [Was geschieht, wenn die Komponenten Regeln beschädigt sind?](https://msdn.microsoft.com/library/aa372795\(VS.85\).aspx).  
  
##### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>Keine Mischung aus freigegebenen und privaten Ressourcen in einer Komponente  
 Die Verweis Zählung erfolgt auf der Komponentenebene. Folglich ist es unmöglich, private Ressourcen (z. b. eine ausführbare Datei) zu aktualisieren, ohne auch freigegebene Ressourcen zu überschreiben, um freigegebene und private Ressourcen in einer Komponente zu mischen. Dieses Szenario stellt abwärts Kompatibilitätsprobleme dar und schränkt Sie von der Erstellung paralleler Funktionen ein.  
  
 Registrierungs Werte, die zum Registrieren des VSPackage bei verwendet werden, [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] sollten z. b. in einer separaten Komponente gespeichert werden, die von der zum Registrieren des VSPackage bei verwendeten Komponenten getrennt ist [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Freigegebene Dateien oder Registrierungs Werte werden in einer anderen Komponente verwendet.  
  
## <a name="scenario-1-shared-vspackage"></a>Szenario 1: frei gegebenes VSPackage  
 In diesem Szenario wird ein frei gegebenes VSPackage (eine einzelne Binärdatei, die mehrere Versionen von unterstützt [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ) in einem Windows Installer Paket ausgeliefert. Die Registrierung bei jeder Version von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] wird durch Benutzer auswählbare Features gesteuert. Dies bedeutet auch, dass bei Zuweisung zu separaten Features jede Komponente einzeln für die Installation oder die Installation ausgewählt werden kann, sodass der Benutzer die Kontrolle über die Integration des VSPackage in verschiedene Versionen von erhält [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . (Weitere Informationen zur Verwendung von Funktionen in Windows Installer Paketen finden Sie unter [Windows Installer Features](https://msdn.microsoft.com/library/aa372840\(VS.85\).aspx) .)  
  
 ![Grafik zu freigegebenem VS-Paket](../../extensibility/internals/media/vs-sharedpackage.gif "VS_SharedPackage")  
Frei gegebenes VSPackage-Installationsprogramm  
  
 Wie in der Abbildung gezeigt, werden freigegebene Komponenten Teil des Feat_Common Features, das immer installiert ist. Wenn Sie die Feat_VS2002-und Feat_VS2003 Features sichtbar machen, können Benutzer bei der Installation auswählen, in welchen Versionen von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Sie das VSPackage integrieren soll. Benutzer können auch Windows Installer Wartungsmodus verwenden, um Funktionen hinzuzufügen oder zu entfernen. in diesem Fall werden die VSPackage-Registrierungsinformationen aus unterschiedlichen Versionen von hinzugefügt oder entfernt [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
> [!NOTE]
> Wenn Sie die Anzeige Spalte einer Funktion auf 0 festlegen, wird Sie ausgeblendet. Ein Spaltenwert auf niedriger Ebene, z. b. 1, stellt sicher, dass er immer installiert wird. Weitere Informationen finden Sie unter [INSTALLLEVEL-Eigenschaft](https://msdn.microsoft.com/library/aa369536\(VS.85\).aspx) und [Funktions Tabelle](https://msdn.microsoft.com/library/aa368585.aspx).  
  
## <a name="scenario-2-shared-vspackage-update"></a>Szenario 2: frei gegebenes VSPackage-Update  
 In diesem Szenario wird eine aktualisierte Version des VSPackage-Installers in Szenario 1 ausgeliefert. Im Rahmen der Erörterung bietet das Update Unterstützung für [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , aber es kann auch ein einfacherer Sicherheitspatches oder ein Fehler Behebungs Service Pack sein. Windows Installer Regeln für die Installation neuerer Komponenten erfordern, dass unveränderte Komponenten, die bereits auf dem System vorhanden sind, nicht neu kopiert werden. In diesem Fall überschreibt ein System mit der Version 1,0, das bereits vorhanden ist, die aktualisierten Komponenten Comp_MyVSPackage.dll und ermöglicht es Benutzern, die neue Funktion Feat_VS2005 mit der Komponente Comp_VS2005_Reg hinzuzufügen.  
  
> [!CAUTION]
> Wenn ein VSPackage von mehreren Versionen von gemeinsam genutzt wird [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , ist es von entscheidender Bedeutung, dass nachfolgende Versionen des VSPackage die Abwärtskompatibilität mit früheren Versionen von aufrechterhalten [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Wenn Sie die Abwärtskompatibilität nicht beibehalten können, müssen Sie parallele private VSPackages verwenden. Weitere Informationen finden Sie [unter unterstützen mehrerer Versionen von Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).  
  
 ![Bild zur Aktualisierung von freigegebenem VS-Paket](../../extensibility/internals/media/vs-sharedpackageupdate.gif "VS_SharedPackageUpdate")  
Installer für freigegebene VSPackage-Updates  
  
 Dieses Szenario stellt ein neues VSPackage-Installationsprogramm dar und nutzt die Unterstützung von Windows Installer für kleinere Upgrades. Benutzer installieren einfach Version 1,1 und aktualisieren Version 1,0. Es ist jedoch nicht erforderlich, Version 1,0 auf dem System zu haben. Das gleiche Installationsprogramm installiert Version 1,1 auf einem System ohne Version 1,0. Der Vorteil der Bereitstellung von geringfügigen Upgrades auf diese Weise besteht darin, dass es nicht notwendig ist, ein Upgrade-Installationsprogramm und ein voll Produkt Installationsprogramm zu entwickeln. Ein Installer führt beide Aufträge aus. Eine Sicherheitslösung oder Service Pack kann stattdessen Windows Installer Patches nutzen. Weitere Informationen finden Sie unter [Patching und Upgrades](https://msdn.microsoft.com/library/aa370579\(VS.85\).aspx).  
  
## <a name="scenario-3-side-by-side-vspackage"></a>Szenario 3: paralleles VSPackage  
 In diesem Szenario werden zwei VSPackage-Installationsprogramme dargestellt – eine für jede Version von Visual Studio .NET 2003 und [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Jedes Installationsprogramm installiert ein paralleles oder privates VSPackage (eines, das speziell für eine bestimmte Version von erstellt und installiert wurde [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ). Jedes VSPackage befindet sich in seiner eigenen Komponente. Folglich kann jeder einzeln mit Patches oder Wartungs Releases gewartet werden. Da die VSPackage-dll jetzt Versions spezifisch ist, ist es sicher, dass Sie Ihre Registrierungsinformationen in dieselbe Komponente wie die dll einschließen.  
  
 ![Vs-Seite&#45;durch&#45;Seite im Vergleich zu Paketen](../../extensibility/internals/media/vs-sbys-package.gif "VS_SbyS_Package")  
Seite-an-Seite-VSPackage-Installer  
  
 Jedes Installationsprogramm enthält auch Code, der von den beiden Installationsprogrammen gemeinsam genutzt wird. Wenn der freigegebene Code an einem gemeinsamen Speicherort installiert ist, wird der freigegebene Code durch die Installation beider MSI-Dateien nur einmal installiert. Der zweite Installer erhöht lediglich einen Verweis Zähler für die Komponente. Der Verweis Zähler stellt sicher, dass, wenn eines der VSPackages deinstalliert wird, der freigegebene Code für das andere VSPackage beibehalten wird. Wenn das zweite VSPackage ebenfalls deinstalliert wird, wird der freigegebene Code entfernt.  
  
## <a name="scenario-4-side-by-side-vspackage-update"></a>Szenario 4: paralleles VSPackage-Update  
 In diesem Szenario hat das VSPackage für [!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)] eine Sicherheitslücke verursacht, und Sie müssen ein Update ausgeben. Wie in Szenario 2 können Sie eine neue MSI-Datei erstellen, mit der eine vorhandene Installation aktualisiert wird, die die Sicherheitskorrektur umfasst, und neue Installationen mit dem bereits vorhandenen Sicherheits Fix bereitstellen.  
  
 In diesem Fall ist das VSPackage ein verwaltetes VSPackage, das im globalen Assemblycache (GAC) installiert ist. Wenn Sie die Lösung neu erstellen, um den Sicherheitsfehler einzuschließen, müssen Sie den Revisionsnummern Teil der Versionsnummer der Assembly ändern. Die Registrierungsinformationen für die neue Assemblyversionsnummer überschreiben die vorherige Version, wodurch [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] die Assembly geladen wird.  
  
 ![Vs-Seite&#45;durch&#45;Seite mit der vs-Paket Update Grafik](../../extensibility/internals/media/vs-sbys-packageupdate.gif "VS_SbyS_PackageUpdate")  
Paralleles VSPackage-Update Installationsprogramm  
  
 **Hinweis** Weitere Informationen zur Bereitstellung von parallelen Assemblys finden Sie unter [vereinfachen der Bereitstellung und lösen der DLL-Hell mit dem .NET Framework](https://msdn.microsoft.com/library/ms973843.aspx).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Windows Installer](https://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [Unterstützen mehrerer Versionen von Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)
