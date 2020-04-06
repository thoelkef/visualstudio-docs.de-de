---
title: Quellcodeverwaltung VSPackage-Architektur | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, architecture
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d6e62aa9e2d725e982f0605e2721f0bfeb3cc5ee
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705085"
---
# <a name="source-control-vspackage-architecture"></a>Architektur von Quellcodeverwaltungs-VSPackages
Ein Quellcodeverwaltungspaket ist ein VSPackage, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] das dienste verwendet, die die IDE bereitstellt. Im Gegenzug stellt ein Quellcodeverwaltungspaket seine Funktionalität als Quellcodeverwaltungsdienst bereit. Darüber hinaus ist ein Quellcodeverwaltungspaket eine vielseitigere Alternative als ein [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Quellcodeverwaltungs-Plug-In für die Integration der Quellcodeverwaltung in .

 Ein Quellcodeverwaltungs-Plug-In, das die Quellcodeverwaltungs-Plug-In-API implementiert, hält sich an einen strengen Vertrag. Beispielsweise kann ein Plug-In die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Standardbenutzeroberfläche (UI) nicht ersetzen. Darüber hinaus ermöglicht die Quellcodeverwaltungs-Plug-In-API kein Plug-In, um ein eigenes Quellcodeverwaltungsmodell zu implementieren. Ein Quellcodeverwaltungspaket überwindet jedoch diese beiden Einschränkungen. Ein Quellcodeverwaltungspaket hat die vollständige Kontrolle über [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] die Quellcodeverwaltungserfahrung eines Benutzers. Darüber hinaus kann ein Quellcodeverwaltungspaket sein eigenes Quellcodeverwaltungsmodell und seine eigene Logik verwenden und alle Quellcodeverwaltungs-bezogenen Benutzeroberflächen definieren.

## <a name="source-control-package-components"></a>Source-Control-Paketkomponenten
 Wie im Architekturdiagramm gezeigt, ist eine [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Komponente mit dem Namen Source Control Stub [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ein VSPackage, das ein Quellcodeverwaltungspaket mit integriert.

 Source Control Stub verarbeitet die folgenden Aufgaben.

- Stellt die allgemeine Benutzeroberfläche bereit, die für die Registrierung von Quellcodeverwaltungspaketen erforderlich ist.

- Lädt ein Quellcodeverwaltungspaket.

- Legt ein Quellcodeverwaltungspaket als aktiv/inaktiv fest.

  Source Control Stub sucht nach dem aktiven Dienst für das Quellcodeverwaltungspaket und leitet alle eingehenden Dienstaufrufe von der IDE an dieses Paket weiter.

  Das Quellcodeverwaltungsadapterpaket ist ein spezielles [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Quellcodeverwaltungspaket, das dies ermöglicht. Dieses Paket ist die zentrale Komponente für die Unterstützung von Quellcodeverwaltungs-Plug-Ins basierend auf der Quellcodeverwaltungs-Plug-In-API. Wenn ein Quellcodeverwaltungs-Plug-In das aktive Plug-In ist, sendet der Quellcodeverwaltungsstub seine Ereignisse an das Quellcodeverwaltungsadapterpaket. Das Quellcodeverwaltungsadapterpaket wiederum kommuniziert mithilfe der Quellcodeverwaltungs-Plug-In-API mit dem Quellcodeverwaltungs-Plug-In und stellt außerdem eine Standardbenutzeroberfläche bereit, die für alle Quellcodeverwaltungs-Plug-Ins üblich ist.

  Wenn ein Quellcodeverwaltungspaket das aktive Paket ist, kommuniziert der Quellcodeverwaltungsstub hingegen direkt [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] mit dem Paket über die Source-Control Package-Schnittstellen. Das Quellcodeverwaltungspaket ist für das Hosten seiner eigenen Quellcodeverwaltungsbenutzeroberfläche verantwortlich.

  ![Grafik zur Quellverwaltungsarchitektur](../../extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")

  Für ein [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Quellcodeverwaltungspaket, bietet keinen Quellcodeverwaltungscode oder eine API für die Integration. Vergleichen Sie dies mit dem unter [Erstellen eines Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/creating-a-source-control-plug-in.md) beschriebenen Ansatz, bei dem das Quellcodeverwaltungs-Plug-In einen starren Satz von Funktionen und Rückrufen implementieren muss.

  Wie jedes VSPackage ist ein Quellcodeverwaltungspaket ein COM-Objekt, das mithilfe `CoCreateInstance`von erstellt werden kann. Das VSPackage stellt sich [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>IDE durch Implementierung von zur Verfügung. Wenn eine Instance erstellt wurde, empfängt ein VSPackage <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> einen Sitezeiger und eine Schnittstelle, die dem VSPackage Zugriff auf die verfügbaren Dienste und Schnittstellen in der IDE bietet.

  Das Schreiben eines VSPackage-basierten Quellcodeverwaltungspakets erfordert erweiterteprogrammierliche Kenntnisse als das Schreiben eines Source Control Plug-in-API-basierten Plug-Ins.

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- [Erste Schritte](../../extensibility/internals/getting-started-with-source-control-vspackages.md)
