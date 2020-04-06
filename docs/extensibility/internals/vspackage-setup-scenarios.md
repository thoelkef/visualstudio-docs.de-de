---
title: VSPackage-Setup-Szenarien | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, deployment considerations
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 01279666642adb729d4350b8a497c42d78159120
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703977"
---
# <a name="vspackage-setup-scenarios"></a>VSPackage-Setupszenarien

Es ist wichtig, Ihr VSPackage-Installationsprogramm für Flexibilität zu entwerfen. Beispielsweise müssen Sie in Zukunft möglicherweise einen Sicherheitspatch veröffentlichen, oder Sie können eine Geschäftsstrategie ändern, die eine gründliche Unterstützung bei der Seitenversionierung erfordert.

Unter [Unterstützung mehrerer Versionen von Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)können Sie sich über die Vorteile [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] und Probleme der Unterstützung von nebeneinander gehenden Installationen mit gemeinsam genutzten oder nebeneinander befindlichen Installationen Ihres VSPackage informieren. Kurz gesagt, side-by-side VSPackages bieten Ihnen die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]größte Flexibilität, um neue Funktionen von zu unterstützen.

Die in diesem Thema behandelten Szenarien sind nicht Ihre einzigen Optionen, sondern werden als empfohlene bewährte Methoden dargestellt.

## <a name="components-privacy-and-sharing"></a>Komponenten, Datenschutz und Freigabe

### <a name="make-your-components-independent"></a>Machen Sie Ihre Komponenten unabhängig

Nachdem Sie eine Komponente identifiziert und `GUID`aufgepopt, eine zugewiesen und die Komponente bereitgestellt haben, können Sie ihre Zusammensetzung nicht mehr ändern. Wenn Sie die Zusammensetzung einer Komponente ändern, muss die resultierende `GUID`Komponente eine neue Komponente mit einer neuen sein. Angesichts dieser Tatsachen wird die größte Versionsflexibilität durch die Unabhängigkeit jeder Komponente und einer eigenständigen Einheit ermöglicht. Weitere Informationen zu Regeln für Komponenten finden Sie unter [Ändern des Komponentencodes](/windows/desktop/Msi/changing-the-component-code) und [Was passiert, wenn die Komponentenregeln gebrochen sind?](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken).

### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>Mischen Sie keine freigegebenen und privaten Ressourcen in einer Komponente

Die Referenzzählung erfolgt auf Komponentenebene. Das Mischen freigegebener und privater Ressourcen in einer Komponente macht es daher unmöglich, private Ressourcen, z. B. eine ausführbare Datei, zu aktualisieren, ohne auch freigegebene Ressourcen zu überschreiben. Dieses Szenario verursacht Probleme mit der Abwärtskompatibilität und hindert Sie daran, nebeneinander Funktionen zu erstellen.

Beispielsweise sollten Registrierungswerte, die zum Registrieren [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Ihres VSPackage mit dem verwendet werden, in einer Komponente getrennt von einer Komponente aufbewahrt werden, die zum Registrieren Ihres VSPackage bei Visual Studio verwendet wird. Freigegebene Dateien oder Registrierungswerte werden in einer weiteren Komponente gespeichert.

## <a name="scenario-1-shared-vspackage"></a>Szenario 1: Freigegebenes VSPackage

In diesem Szenario wird ein freigegebenes VSPackage (eine einzelne Binärdatei, die mehrere Versionen von Visual Studio unterstützt) in einem Windows Installer-Paket ausgeliefert. Die Registrierung bei jeder Version von Visual Studio wird durch vom Benutzer wählbare Features gesteuert. Es bedeutet auch, dass, wenn sie separaten Features zugewiesen wird, jede Komponente einzeln für die Installation oder [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Deinstallation ausgewählt werden kann, wodurch der Benutzer die Kontrolle über die Integration des VSPackage in verschiedene Versionen von hat. (Weitere Informationen zur Verwendung von Features in Windows Installer-Paketen finden Sie unter [Windows Installer-Features.)](/windows/desktop/Msi/windows-installer-features)

![VS Freigegebenes VSPackage-Installationsprogramm](../../extensibility/internals/media/vs_sharedpackage.gif "VS_SharedPackage")

Wie in der Abbildung gezeigt, werden gemeinsam genutzte Komponenten Teil des Feat_Common-Funktion, das immer installiert ist. Indem benutzer die Feat_VS2002- und Feat_VS2003-Features sichtbar machen, können sie bei der Installation auswählen, in welche Versionen von Visual Studio das VSPackage integriert werden soll. Benutzer können den Windows Installer-Wartungsmodus auch verwenden, um Features hinzuzufügen oder zu entfernen, wodurch in diesem Fall die VSPackage-Registrierungsinformationen aus verschiedenen Versionen von Visual Studio hinzugefügt oder entfernt werden.

> [!NOTE]
> Wenn Sie die Spalte Anzeige eines Features auf 0 festlegen, wird sie ausgeblendet. Ein niedriger Level-Spaltenwert, z. B. 1, stellt sicher, dass er immer installiert wird. Weitere Informationen finden Sie unter [INSTALLLEVEL-Eigenschaft](/windows/desktop/Msi/installlevel) und [Feature-Tabelle](/windows/desktop/Msi/feature-table).

## <a name="scenario-2-shared-vspackage-update"></a>Szenario 2: Freigegebenes VSPackage-Update

In diesem Szenario wird eine aktualisierte Version des VSPackage-Installationsprogramms in Szenario 1 ausgeliefert. Zur Diskussion summiert sich das Update mit Unterstützung für Visual Studio, aber es könnte auch ein einfacherer Sicherheitspatch oder ein Fehlerbehebungs-Service Pack sein. Die Regeln von Windows Installer für die Installation neuerer Komponenten erfordern, dass unveränderte Komponenten, die sich bereits auf dem System befinden, nicht erneut kopiert werden. In diesem Fall überschreibt ein System mit Version 1.0 bereits die aktualisierte Komponente Comp_MyVSPackage.dll und lässt Benutzer die neue Funktion Feat_VS2005 mit ihrer Komponente Comp_VS2005_Reg hinzufügen.

> [!CAUTION]
> Wenn ein VSPackage von mehreren [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Versionen von freigegeben wird, ist es wichtig, dass nachfolgende Versionen des VSPackage die Abwärtskompatibilität mit früheren Versionen von Visual Studio aufrechterhalten. Wenn Sie die Abwärtskompatibilität nicht aufrechterhalten können, müssen Sie nebeneinander private VSPackages verwenden. Weitere Informationen finden Sie unter [Unterstützung mehrerer Versionen von Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).

![INSTALLATIONSprogramm FÜR DAS freigegebene VS-Paketupdate](../../extensibility/internals/media/vs_sharedpackageupdate.gif "VS_SharedPackageUpdate")

In diesem Szenario wird ein neues VSPackage-Installationsprogramm angezeigt, das die Unterstützung von Windows Installer für kleinere Upgrades nutzt. Benutzer installieren einfach Version 1.1 und es aktualisiert Version 1.0. Es ist jedoch nicht erforderlich, Version 1.0 auf dem System zu haben. Das gleiche Installationsprogramm installiert Version 1.1 auf einem System ohne Version 1.0. Der Vorteil, kleinere Upgrades auf diese Weise bereitzustellen, ist, dass es nicht notwendig ist, die Arbeit der Entwicklung eines Upgrade-Installers und eines Vollprodukt-Installers zu durchlaufen. Ein Installateur macht beide Aufgaben. Ein Sicherheitsupdate oder Service Pack kann stattdessen windows Installer-Patches nutzen. Weitere Informationen finden Sie unter [Patching und Upgrades](/windows/desktop/Msi/patching-and-upgrades).

## <a name="scenario-3-side-by-side-vspackage"></a>Szenario 3: Side-by-Side VSPackage

In diesem Szenario werden zwei VSPackage-Installationsprogramme vorgestellt – eine für jede Version von Visual Studio .NET 2003 und Visual Studio. Jedes Installationsprogramm installiert ein nebeneinander stehendes oder privates VSPackage (eines, das speziell für eine bestimmte Version von Visual Studio erstellt und installiert wurde). Jedes VSPackage befindet sich in einer eigenen Komponente. Somit kann jeder individuell mit Patches oder Wartungsfreigaben gewartet werden. Da die VSPackage-DLL jetzt versionsspezifisch ist, ist es sicher, ihre Registrierungsinformationen in dieselbe Komponente wie die DLL einzuschließen.

![VS Side-by-Side VS Paketinstallationsprogramm](../../extensibility/internals/media/vs_sbys_package.gif "VS_SbyS_Package")

Jedes Installationsprogramm enthält auch Code, der von den beiden Installationsprogrammen gemeinsam genutzt wird. Wenn der freigegebene Code an einem gemeinsamen Speicherort installiert ist, wird der freigegebene Code nur einmal installiert, wenn beide MSI-Dateien installiert werden. Das zweite Installationsprogramm erhöht lediglich eine Referenzanzahl für die Komponente. Die Verweisanzahl stellt sicher, dass der freigegebene Code für das andere VSPackage verbleibt, wenn eines der VSPackages deinstalliert wird. Wenn auch das zweite VSPackage deinstalliert wird, wird der freigegebene Code entfernt.

## <a name="scenario-4-side-by-side-vspackage-update"></a>Szenario 4: Side-by-Side-VSPackage-Aktualisierung

In diesem Szenario litt Ihr VSPackage für Visual Studio unter einer Sicherheitslücke, und Sie müssen ein Update ausstellen. Wie in Szenario 2 können Sie eine neue MSI-Datei erstellen, die eine vorhandene Installation aktualisiert, um das Sicherheitsupdate einzuschließen, sowie neue Installationen mit dem bereits vorhandenen Sicherheitsupdate bereitstellen.

In diesem Fall ist das VSPackage ein verwaltetes VSPackage, das im globalen Assemblycache (GAC) installiert ist. Wenn Sie sie neu erstellen, um den Sicherheitspatch einzuschließen, müssen Sie den Teil der Revisionsnummer der Assemblyversionsnummer ändern. Die Registrierungsinformationen für die neue Assemblyversionsnummer überschreiben die vorherige Version, wodurch [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] die feste Assembly geladen wird.

![VS Side-by-Side VS-Paketaktualisierungsinstallationsprogramm](../../extensibility/internals/media/vs_sbys_packageupdate.gif "VS_SbyS_PackageUpdate")

Weitere Informationen zum Bereitstellen von nebeneinander anseitigen Assemblys finden Sie unter [Vereinfachen der Bereitstellung und Lösen von DLL-Hölle mit .NET Framework](https://msdn.microsoft.com/library/ms973843.aspx).

## <a name="see-also"></a>Weitere Informationen

- [Windows Installer](/windows/desktop/Msi/windows-installer-portal)
- [Unterstützen mehrerer Versionen von Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)
