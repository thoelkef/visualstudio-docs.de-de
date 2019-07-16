---
title: Datenquelle der Architektur des VSPackage-Steuerelements | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, architecture
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c05ae692a364d4e7a81a017d376dd820ade56b73
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322503"
---
# <a name="source-control-vspackage-architecture"></a>Architektur von Quellcodeverwaltungs-VSPackages
Ein Paket für die quellcodeverwaltung ist eine VSPackage, das verwendet Dienste, die die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE bietet. Im Gegenzug stellt ein Paket für die quellcodeverwaltung seine Funktionalität als einen quellcodeverwaltungsdienst bereit. Darüber hinaus ist ein Paket für die quellcodeverwaltung als ein Quellcodeverwaltungs-Plug-In für die Integration der quellcodeverwaltung in eine stärker ausbauen Alternative [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

 Hält einen strengen Vertrag ein Quellcodeverwaltungs-Plug-in, der die Source-Plug-in-API implementiert. Beispielsweise ein plug-in kann nicht ersetzen Sie die standardmäßige [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Benutzeroberfläche (UI). Darüber hinaus kann nicht die Source-Plug-in-API für ein plug-in, um eine eigene quellcodeverwaltungmodell implementieren werden. Ein Paket quellcodeverwaltung überwindet jedoch diese beiden Einschränkungen. Ein Paket für die quellcodeverwaltung hat vollständige Kontrolle über die Quelle Steuerelement benutzerfreundlichkeit ein [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Benutzer. Darüber hinaus kann ein Paket für die quellcodeverwaltung verwenden, eigene quellcodeverwaltungmodell und Logik, und es kann alle vorhandenen Benutzer-Quellschnittstellen definieren.

## <a name="source-control-package-components"></a>Quellcodeverwaltung-Paketkomponenten
 Siehe das Architekturdiagramm einer [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Komponente, die mit dem Namen der Quellcode-Verwaltungsstub ist ein VSPackage, das ein Paket der quellcodeverwaltung mit integriert [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

 Quellcode-Verwaltungsstub behandelt die folgenden Aufgaben.

- Stellt die allgemeine Benutzeroberfläche, die für die quellcodeverwaltung paketregistrierung erforderlich ist.

- Lädt ein Paket für die quellcodeverwaltung.

- Ein Paket für die quellcodeverwaltung festgelegt als aktiv/inaktiv.

  Quellcode-Verwaltungsstub sucht nach dem aktiven Dienst für das Paket für die quellcodeverwaltung und leitet alle eingehenden Dienstaufrufe, aus der IDE, die dem Paket.

  Das Quellcodeverwaltungspaket-Adapter ist ein spezielles Datenquellen-Steuerelement zu verpacken, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] enthält. Dieses Paket ist die zentrale Komponente für die Unterstützung von Quellcodeverwaltungs-Plug-ins basierend auf der Source-Plug-in-API. Wenn ein Quellcodeverwaltungs-Plug-in den aktiven-Plug-in ist, sendet der Quellcode-Verwaltungsstub der Ereignisse an das Quellcodeverwaltungspaket-Adapter. Im Gegenzug das Quellcodeverwaltungspaket-Adapter kommuniziert mit das Quellcodeverwaltungs-Plug-in, indem Sie mit der Source-Plug-in-API und stellt auch eine Benutzeroberfläche, die für alle Quellcodeverwaltungs-Plug-ins ist.

  Wenn ein Paket für die quellcodeverwaltung aktiven Pakets ist, auf der anderen Seite der Quellcode-Verwaltungsstub kommuniziert direkt mit dem Paket mithilfe der [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Source-Control-Paket-Schnittstellen. Die quellcodeverwaltung-Paket ist ein eigene Benutzeroberfläche des Datenquellen-Steuerelement hostet.

  ![Architektur des Steuerelements Quellgrafik](../../extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")

  Für ein Paket quellcodeverwaltung [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] stellt keinen Quellcode-Steuerelement oder eine API zur Integration. Vergleichen Sie dies mit dem Ansatz beschrieben, die in [ein Datenquellen-Steuerelement-Plug-in erstellen](../../extensibility/internals/creating-a-source-control-plug-in.md) , in dem das Quellcodeverwaltungs-Plug-in hat eine feste Gruppe von Funktionen und Rückrufe zu implementieren.

  Wie jedem VSPackage ist ein Paket für die quellcodeverwaltung ein COM-Objekt, das erstellt werden kann `CoCreateInstance`. Das VSPackage wird für die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE durch die Implementierung <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>. Wenn eine Instanz erstellt wurde, erhält eine VSPackage einen Website-Zeiger und eine <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> Schnittstelle, die den VSPackage-Zugriff auf die verfügbaren Dienste und Schnittstellen in der IDE bereitstellt.

  Schreiben ein VSPackage-basierte quellcodeverwaltung Paket erfordert Erweiterte Programmierung Kenntnisse als das Schreiben einer Source Control-Plug-in-API-basierte-Plug-in.

## <a name="see-also"></a>Siehe auch
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- [Erste Schritte](../../extensibility/internals/getting-started-with-source-control-vspackages.md)