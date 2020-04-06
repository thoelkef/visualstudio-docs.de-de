---
title: Übersicht über Konfigurationsoptionen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations
- configuration options, about configuration options
ms.assetid: f4ad4dd3-b39e-42df-ad89-d403cdf24a2b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6d5ac25fcef7b942b791402baf17982c9810e92a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709411"
---
# <a name="configuration-options-overview"></a>Übersicht über Konfigurationsoptionen
Projekte [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] in können mehrere Konfigurationen unterstützen, die erstellt, gedebuggt, ausgeführt und/oder bereitgestellt werden können. Eine Konfiguration ist ein Buildtyp, der mit einem benannten Satz von Eigenschaften, in der Regel Compilerwechseln und Dateispeicherorten, beschrieben wird. Standardmäßig enthalten neue Lösungen zwei Konfigurationen, *Debug* und *Release*. Diese Konfigurationen können mit ihren Standardeinstellungen angewendet oder an Ihre spezifischen Projektmappen- und/oder Projektanforderungen angepasst werden. Einige Pakete können auf zwei Arten erstellt werden: als ActiveX-Editor oder als direkt installierte Komponente. Projekte müssen jedoch nicht mehrere Konfigurationen unterstützen. Wenn nur eine Konfiguration verfügbar ist, wird diese Konfiguration allen Lösungskonfigurationen zugeordnet.

 Konfigurationen bestehen in der Regel aus zwei Teilen: dem Konfigurationsnamen (z. B. *Debug* oder *Release*) und den Plattformeinstellungen. Der Plattformname einer Konfiguration identifiziert die Umgebung, auf die die Konfigurationsziele, z. B. einen API-Satz oder eine Betriebssystemplattform, abzielt. Benutzer [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] von können keine Plattform erstellen; sie müssen aus der Auswahl wählen, die ein Projekt, das VSPackage zulässt. Wenn ein Benutzer ein VSPackage installiert, kann die Bereitstellungsplattform, die während der Entwicklung des Pakets erstellt wurde, jeden gewünschten Plattformnamen basierend auf den vom Paketersteller festgelegten Kriterien anzeigen. Der Benutzer kann dann aus der Liste der Plattformen auswählen, die über das VSPackage zur Verfügung gestellt werden, wenn die Eigenschaftenseiten instanziiert werden.

 Plattformnamen sind optional, da nicht alle Projekte das Konzept der Plattformen unterstützen. Wenn eine Konfiguration keinen Plattformnamen hat, wird die Zeichenfolge **N/A** in der Benutzeroberfläche angezeigt.

 Jede Lösung verfügt über einen eigenen Satz von Konfigurationen, von denen jeweils nur eine aktiv sein kann. Eine Projektmappenkonfiguration besteht aus einem Satz von nicht mehr als einer Konfiguration aus jedem Projekt. Die "nicht mehr als"-Bestimmung ist auf die Option zurückzuführen, ein Projekt von einer Projektmappenkonfiguration auszuschließen. Benutzer können eigene benutzerdefinierte Lösungskonfigurationen erstellen.

 Die folgende Tabelle veranschaulicht die typischen Konfigurationen für ein Projekt. Die Zeilen sind mit Konfigurationsnamen und die Spalten mit Plattformnamen beschriftet.

|Konfigurationsname|Plattform: Win32|Plattform: Win64|
|------------------------|----------------------|----------------------|
|*Debuggen*|\<Debug Win32-Einstellungen>|\<Debug Win64-Einstellungen>|
|*Release*|\<Freigeben von Win32-Einstellungen>|\<Freigeben von Win64-Einstellungen>|
|*MyConfig*|Nicht zutreffend|\<MyConfig Win64-Einstellungen>|

> [!NOTE]
> Sie können keine *MyConfig-Lösungskonfiguration* erstellen, die eine Win32-Plattform ausschließt, es sei denn, das Projekt, auf das Sie abzielen, unterstützt Win32 nicht.

 Wenn Sie die aktive Konfiguration für eine Projektmappe ändern, wird der Satz von Projektkonfigurationen ausgewählt, die in dieser Projektmappe erstellt, ausgeführt, gedebuggt oder bereitgestellt werden. Wenn Sie beispielsweise die Konfiguration der aktiven Projektmappe von *Release* in *Debug*ändern, werden alle Projekte innerhalb dieser Projektmappe automatisch mit der in der Debugkonfiguration der Projektmappe angegebenen Projektkonfiguration erstellt. Die Konfigurationen der Projekte werden auch *Als Debug* bezeichnet, es sei denn, der Benutzer hat manuelle Änderungen im Configuration Manager der Umgebung vorgenommen.

 Zu den für jedes Projekt gespeicherten Lösungskonfigurationseigenschaften gehören der Projektname, der Projektkonfigurationsname, Flags zum Angeben, ob erstellt oder bereitgestellt werden soll, und der Plattformname. Weitere Informationen finden Sie unter [Lösungskonfiguration](../../extensibility/internals/solution-configuration.md).

 Der Benutzer kann Lösungskonfigurationsparameter anzeigen und festlegen, indem er die Projektmappe in der Hierarchie (Projektmappen-Explorer) auswählt und die Eigenschaftenseiten öffnet. Ebenso können Sie Projektkonfigurationsparameter anzeigen und festlegen, indem Sie ein Projekt im Projektmappen-Explorer auswählen und die Eigenschaftenseiten für dieses Projekt öffnen.

 Der Benutzer kann auch ein Projekt mit Release-Konfigurationseinstellungen und den Rest mit Debugkonfigurationseinstellungen bei Bedarf erstellen. Weitere Informationen finden Sie unter [Projektkonfiguration zum Erstellen](../../extensibility/internals/project-configuration-for-building.md).

 Das folgende Diagramm zeigt, wie die Schnittstellen implementiert werden, die Projektmappen- und Projektkonfigurationen unterstützen:

 ![Grafik der Konfigurationsschnittstellen](../../extensibility/internals/media/vsconfiginterfaces.gif "vsConfigInterfaces") Konfigurationsschnittstellen

 Einige Anmerkungen zum vorherigen Diagramm:

- `IDispatch`ist im Konfigurationsobjekt als optional markiert. Insbesondere ist es optional, die Konfigurationsschnittstellen für das Suchobjekt zu haben.

- `IVsDebuggableProjectCfg`ist im Konfigurationsobjekt als optional markiert, ist jedoch für die Debugunterstützung erforderlich.

- `IVsProjectCfg2`ist im Konfigurationsobjekt als optional markiert, wird jedoch für die Unterstützung der Ausgabegruppierung benötigt.

- Das Config Provider-Objekt ist als optionales Objekt markiert, aber die Option ist, wo es implementiert werden soll. Sie können das Objekt für das Projektobjekt oder für ein separates Objekt implementieren.

- `IVsCfgProvider2`für die Plattformunterstützung und Konfigurationsbearbeitung erforderlich ist. `IVsCfgProvider`ist ausreichend, wenn Sie diese Funktionalität nicht implementieren.

- Einige dieser Objekte, die im Diagramm als separate Objekte dargestellt werden, können in derselben Klasse kombiniert werden, in der sie auf der Grundlage Ihrer spezifischen Entwurfsanforderungen praktisch sind. In anderen Themen dieses Abschnitts werden jedoch die mit diesen Objekten verknüpften Objekte und Schnittstellen entsprechend dem im Diagramm dargestellten Szenario erörtert.

- Bestimmte Objekte werden separat implementiert. Beispielsweise erfolgt die Projekt- und Projektmappenerstellung auf separaten Threads, und das Objekt, das den Build verwaltet, lebt getrennt von dem Objekt, das die Konfiguration für den Build beschreibt.

  Weitere Informationen zu den Konfigurationsobjektschnittstellen und Konfigurationsanbieterobjektschnittstellen im vorherigen Diagramm finden Sie unter [Projektkonfigurationsobjekt](../../extensibility/internals/project-configuration-object.md). Darüber hinaus enthält die [Projektkonfiguration für](../../extensibility/internals/project-configuration-for-building.md) das Erstellen weitere Informationen zu den Schnittstellen Configuration Builder und Buildabhängigkeitsobjekt, und die [Projektkonfiguration für](../../extensibility/internals/project-configuration-for-managing-deployment.md) die Verwaltung der Bereitstellung beschreibt die Schnittstellen, die an die Konfigurationsbereitstellung sende- und Bereitstellungsabhängigkeitsobjekte angefügt sind. Schließlich beschreibt die [Projektkonfiguration für](../../extensibility/internals/project-configuration-for-output.md) die Ausgabe die Schnittstellen für Ausgabegruppen und Ausgabeobjekt sowie die Verwendung von Eigenschaftenseiten zum Anzeigen und Festlegen konfigurationsabhängiger Eigenschaften.

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>
- [Projektkonfiguration für das Erstellen](../../extensibility/internals/project-configuration-for-building.md)
- [Lösungskonfiguration](../../extensibility/internals/solution-configuration.md)
