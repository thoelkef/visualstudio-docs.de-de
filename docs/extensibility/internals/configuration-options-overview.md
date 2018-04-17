---
title: Konfigurationsoptionen (Übersicht) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project configurations
- configuration options, about configuration options
ms.assetid: f4ad4dd3-b39e-42df-ad89-d403cdf24a2b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 85ee328b278ef9eb1d81acfc5a8299920a221e59
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="configuration-options-overview"></a>Optionen (Übersicht)
Projekten [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] unterstützen mehrere Konfigurationen, die von einer debuggten, ausführen und/oder bereitgestellten erstellt werden können. Eine Konfiguration handelt es sich um einen Buildtyp mit einer benannten Menge von Eigenschaften, in der Regel Compilerschalter und Dateispeicherorte beschrieben. Neue Projektmappen enthalten standardmäßig zwei Konfigurationen, Debug und Release. Diese Konfigurationen können angewendet werden, deren Standardeinstellungen verwenden oder geändert, um Ihren jeweiligen Lösung und/oder Projekt Anforderungen. Einige Pakete können auf zwei Arten erstellt werden: als ActiveX-Editor oder als eine direkte-Komponente. Projekte müssen nicht mehrere Konfigurationen jedoch unterstützen. Wenn nur eine Konfiguration verfügbar ist, wird die Konfiguration aller Projektmappenkonfigurationen zugeordnet.  
  
 Konfigurationen in der Regel bestehen aus zwei Teilen – der Name der Konfiguration (z. B. Debug- oder Release) und plattformeinstellungen. Eine Konfiguration Plattformname identifiziert die Umgebung, die die Konfiguration ausgerichtet ist, z. B. eine API festgelegt oder die Betriebssystem-Plattform. Benutzer von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] eine Plattform; kann nicht erstellt werden aus der Auswahl müssen sie ein Projekt ermöglicht das VSPackage auswählen. Wenn ein Benutzer installiert ein VSPackage die Übermittlung-Plattform, die während der Entwicklung des Pakets erstellt alle gewünschten Plattformname Oberfläche können basierend auf Kriterien, die durch den Paketersteller festgelegt. Der Benutzer kann dann auswählen, aus der Liste der Plattformen, die durch das VSPackage zur Verfügung gestellt, wenn die Eigenschaftenseiten instanziiert werden.  
  
 Plattformnamen sind optional, da nicht alle Projekte das Konzept der Plattformen unterstützt. Wenn eine Konfiguration nicht über einen Plattformnamen verfügt, wird die Zeichenfolge "n/v" in der Benutzeroberfläche angezeigt.  
  
 Jede Lösung weist einen eigenen Satz von Konfigurationen, von denen nur, die einer gleichzeitig aktiv sein kann. Eine Projektmappenkonfiguration ist ein Satz von nicht mehr als eine Konfiguration aus dem Projekt. Die Bedingung ist "nicht mehr als" ist aufgrund der Option aus, um ein Projekt aus einer Projektmappenkonfiguration ausschließen. Benutzer können eigene benutzerdefinierte Projektmappenkonfigurationen erstellen.  
  
 Die folgende Tabelle zeigt das Setup typische Konfigurationen für ein Projekt. Die Zeilen werden mit dem Konfigurationsnamen und die Spalten mit Plattformnamen bezeichnet.  
  
|Konfigurationsname|Plattform – Win32|Plattform – Win64|  
|------------------------|----------------------|----------------------|  
|Debug|\<Debug-Win32-Einstellungen >|\<Debuggen von Win64-Einstellungen >|  
|Release|\<Freigeben von Win32-Einstellungen >|\<Freigeben von Win64-Einstellungen >|  
|MyConfig|Nicht zutreffend|\<MyConfig Win64-Einstellungen >|  
  
> [!NOTE]
>  Sie können keine Projektmappenkonfiguration "MyConfig" erstellen, die eine Plattform "Win32" ausschließt, es sei denn, das Projekt, das das Ziel Win32 nicht unterstützt.  
  
 Ändern die aktive Konfiguration für eine Projektmappe, wählt der Satz von Projektkonfigurationen, die erstellt, ausführen, Debuggen oder bereitgestellt werden in dieser Lösung aus. Wenn Sie die aktive Projektmappenkonfiguration Herausgabe Debuggen ändern, werden alle Projekte in der Projektmappe z. B. automatisch mit der Projekte-Konfiguration, die in der Projektmappe Debug-Konfiguration angegebenen erstellt. Die Projekte-Konfigurationen sind in der Regel auch benannte Debuggen, wenn der Benutzer manuell Änderungen in der Umgebung-Konfigurations-Manager vorgenommen wurde.  
  
 Die Lösung Konfigurationseigenschaften für jedes Projekt gespeichert enthalten den Projektnamen, Projektkonfigurationsname Flags an, ob zum Erstellen oder zum Bereitstellen und Plattformnamen. Weitere Informationen finden Sie unter [Projektmappenkonfiguration](../../extensibility/internals/solution-configuration.md).  
  
 Der Benutzer kann anzeigen und Festlegen von Konfigurationsparameter die Lösung in der Hierarchie (Projektmappen-Explorer) auswählen, und öffnen die Eigenschaftenseiten für Projektmappen. Auf ähnliche Weise können Sie anzeigen und Festlegen von Konfigurationsparameter Projekt wählen Sie im Projektmappen-Explorer das Projekt, und öffnen die Eigenschaftenseiten für das betreffende Projekt.  
  
 Der Benutzer kann auch ein Projekt mit Einstellungen für Releasekonfiguration und die restlichen Einstellungen für Debugkonfiguration bei Bedarf erstellen. Weitere Informationen finden Sie unter [Projektkonfiguration zum Erstellen von](../../extensibility/internals/project-configuration-for-building.md).  
  
 Das folgende Diagramm zeigt, wie die Schnittstellen, die Unterstützung von Projektmappen- und Projektkonfigurationen implementiert werden:  
  
 ![Konfigurationsschnittstellen](../../extensibility/internals/media/vsconfiginterfaces.gif "VsConfigInterfaces")  
Konfigurationsschnittstellen  
  
 Einige Hinweise, die im Zusammenhang mit der vorherigen Abbildung:  
  
-   `IDispatch` wird in das Konfigurationsobjekt als optional gekennzeichnet. Insbesondere ist optional, Sie haben die Konfigurationsschnittstellen auf die Durchsuchen-Objekt.  
  
-   `IVsDebuggableProjectCfg` ist optional, das Konfigurationsobjekt gekennzeichnet, aber für das debugging-Unterstützung ist erforderlich.  
  
-   `IVsProjectCfg2` ist optional, das Konfigurationsobjekt gekennzeichnet, aber für die Ausgabe gruppieren Support benötigt wird.  
  
-   Die `Config Provider` Objekt ist als ein optionales Objekt gekennzeichnet, aber die Option ist, wo Sie sie implementieren. Das Objekt kann auf das Objekt oder ein separates Objekt implementiert werden.  
  
-   `IVsCfgProvider2` für die Plattform-Unterstützung und Bearbeiten der Konfiguration ist erforderlich. `IVsCfgProvider` ist ausreichend, wenn Sie diese Funktion nicht implementieren.  
  
-   Einige dieser Objekte, die im Diagramm angezeigt werden, als separate Objekte in derselben Klasse wo praktikabel kombiniert werden können, basierend auf Ihren bestimmten Designanforderungen. In anderen Themen in diesem Abschnitt werden jedoch die Objekte und Schnittstellen, die diesen Objekten zugeordneten entsprechend in der Abbildung dargestellten Szenario besprochen.  
  
-   Bestimmte Objekte sind getrennt implementiert. Auftreten, z. B. Projekt und Projektmappe Erstellung auf separaten Threads und das Objekt, das die Arbeit mit Build separat aus dem Objekt, beschreibt die Konfiguration für den Build zu verwalten.  
  
 Weitere Informationen zu den Konfigurationsobjekt und Konfigurationsanbieterobjekt Schnittstellen in der vorherigen Abbildung, finden Sie unter [Projekt Konfigurationsobjekt](../../extensibility/internals/project-configuration-object.md). Darüber hinaus [Projektkonfiguration zum Erstellen von](../../extensibility/internals/project-configuration-for-building.md) enthält weitere Informationen über die Configuration-Generator und Erstellen von Dependency-Objekt-Schnittstellen, und [Projektkonfiguration für die Bereitstellung verwalten](../../extensibility/internals/project-configuration-for-managing-deployment.md) Außerdem werden die Schnittstellen beschrieben Bereitsteller Konfiguration und Bereitstellung Abhängigkeitsobjekte zugeordnet. Schließlich [Projektkonfiguration für die Ausgabe](../../extensibility/internals/project-configuration-for-output.md) beschreibt die Ausgabe-Gruppe und Ausgabeobjekt-Schnittstellen, und die Verwendung von Eigenschaftenseiten, um die konfigurationsabhängigen Eigenschaften anzuzeigen und festzulegen.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>   
 [Konfiguration für die Erstellung des Projekts](../../extensibility/internals/project-configuration-for-building.md)   
 [Projektmappenkonfiguration](../../extensibility/internals/solution-configuration.md)