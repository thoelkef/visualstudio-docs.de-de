---
title: VSPackage-Registrierung | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a05dec8fbef40143f31f2c0ac484824717ea2e32
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703918"
---
# <a name="vspackage-registration"></a>VSPackage-Registrierung
VSPackages muss [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ihnen mitteilen, dass sie installiert sind und geladen werden sollten. Dieser Vorgang wird durch das Schreiben von Informationen in der Registrierung durchgeführt. Das ist ein typischer Job eines Installateurs.

> [!NOTE]
> Es ist eine akzeptierte Praxis während der VSPackage-Entwicklung, Selbstregistrierung zu verwenden. [!INCLUDE[vsipprvsip](../../extensibility/includes/vsipprvsip_md.md)] Partner können ihre Produkte jedoch nicht mit Selbstregistrierung als Teil der Einrichtung versenden.

 Registrierungseinträge in einem Windows Installer-Paket werden in der Regel in der Registrierungstabelle vorgenommen. Sie können Dateierweiterungen auch in der Registrierungstabelle registrieren. Windows Installer bietet jedoch integrierte Unterstützung über den programmatischen Bezeichner (ProgId), Klasse, Erweiterung und Verbtabellen. Weitere Informationen finden Sie unter [Datenbanktabellen](/windows/desktop/Msi/database-tables).

 Stellen Sie sicher, dass Ihre Registrierungseinträge der Komponente zugeordnet sind, die für die für die gewählte Side-by-Side-Strategie geeignet ist. Beispielsweise sollten Registrierungseinträge für eine freigegebene Datei der Windows Installer-Komponente dieser Datei zugeordnet werden. Ebenso sollten Registrierungseinträge für eine versionsspezifische Datei der Komponente dieser Datei zugeordnet werden. Andernfalls könnte die Installation oder Deinstallation Ihres [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage für eine Version von IHR VSPackage in anderen Versionen brechen. Weitere Informationen finden Sie unter [Unterstützung mehrerer Versionen von Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).

> [!NOTE]
> Die einfachste Möglichkeit, die Registrierung zu verwalten, besteht darin, dieselben Daten in denselben Dateien sowohl für die Entwicklerregistrierung als auch für die Installationszeitregistrierung zu verwenden. Beispielsweise können einige Installer-Entwicklungstools Dateien im .reg-Format zur Buildzeit verwenden. Wenn Entwickler .reg-Dateien für ihre eigene tägliche Entwicklung und das Debuggen verwalten, können dieselben Dateien automatisch in das Installationsprogramm aufgenommen werden. Wenn Sie Registrierungsdaten nicht automatisch freigeben können, müssen Sie sicherstellen, dass die Kopie der Registrierungsdaten des Installationsprogramms aktuell ist.

## <a name="registering-unmanaged-vspackages"></a>Registrieren von nicht verwalteten VSPackages
 Nicht verwaltete VSPackages (einschließlich der von der Visual Studio-Paketvorlage generierten Dateien) verwenden .rgs-Dateien im ATL-Stil, um Registrierungsinformationen zu speichern. Das .rgs-Dateiformat ist ATL spezifisch und kann in der Regel nicht von einem Installationserstellungstool verwendet werden. Registrierungsinformationen für das VSPackage-Installationsprogramm müssen separat verwaltet werden. Entwickler können beispielsweise Dateien im .reg-Format mit .rgs-Dateiänderungen synchronisieren. Die .reg-Dateien können mit RegEdit für Entwicklungsarbeiten zusammengeführt oder von einem Installationsprogramm verbraucht werden.

## <a name="registering-managed-vspackages"></a>Registrieren von verwalteten VSPackages
 Das RegPkg-Tool liest die Registrierungsattribute aus einem verwalteten VSPackage und kann die Informationen entweder direkt in die Registrierung schreiben oder Dateien im .reg-Format schreiben, die von einem Installationsprogramm verwendet werden können.

> [!NOTE]
> Das RegPkg-Tool ist nicht verteilbar und kann nicht zum Registrieren eines VSPackage auf dem System eines Benutzers verwendet werden.

## <a name="why-vspackages-should-not-self-register-at-install-time"></a>Warum VSPackages sich zur Installationszeit nicht selbst registrieren sollten
 Ihre VSPackage-Installateure sollten sich nicht auf die Selbstregistrierung verlassen. Auf den ersten Blick scheint es eine gute Idee zu sein, die Registrierungswerte eines VSPackage nur im VSPackage selbst zu halten. Da Entwickler die Registrierungswerte benötigen, die für ihre Routinearbeit und Tests verfügbar sind, ist es sinnvoll, die Verwaltung einer separaten Kopie der Registrierungsdaten im Installationsprogramm zu vermeiden. Das Installationsprogramm kann sich beim Schreiben von Registrierungswerten auf das VSPackage selbst verlassen.

 Obwohl sie theoretisch gut ist, weist die Selbstregistrierung mehrere Fehler auf, die sie für die VSPackage-Installation ungeeignet machen:

- Wenn Sie Installation, Deinstallation, Installationsrollback und Deinstallationsrollback korrekt unterstützen, müssen Sie vier benutzerdefinierte Aktionen für jedes verwaltete VSPackage erstellen, das sich selbst registriert, indem RegPkg aufgerufen wird.

- Ihr Ansatz für die Unterstützung von Side-by-Side erfordert möglicherweise, dass Sie vier benutzerdefinierte Aktionen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]erstellen, die RegSvr32 oder RegPkg für jede unterstützte Version von aufrufen.

- Eine Installation mit selbst registrierten Modulen kann nicht sicher zurückgesetzt werden, da es keine Möglichkeit gibt, zu sagen, ob die selbst registrierten Schlüssel von einem anderen Feature oder einer anderen Anwendung verwendet werden.

- Selbstregistrierte DLLs verknüpfen manchmal mit zusätzlichen DLLs, die nicht vorhanden sind oder die falsche Version sind. Im Gegensatz dazu kann Windows Installer DLLs mithilfe der Registrierungstabellen registrieren, ohne vom aktuellen Status des Systems abhängig zu sein.

- Selbstregistrierungscode kann der Zugriff auf Netzwerkressourcen, z. B. Typbibliotheken, verweigert werden, wenn eine Komponente sowohl als Run-from-Source angegeben als auch in der SelfReg-Tabelle aufgeführt ist. Dies kann dazu führen, dass die Installation der Komponente während einer administrativen Installation fehlschlägt.

## <a name="see-also"></a>Weitere Informationen
- [Windows Installer](/windows/desktop/Msi/windows-installer-portal)
- [Managed Package-Registrierung](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)
