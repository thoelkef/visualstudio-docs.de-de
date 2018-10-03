---
title: Übersicht der Konfigurationsoptionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project configurations
- configuration options, about configuration options
ms.assetid: f4ad4dd3-b39e-42df-ad89-d403cdf24a2b
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 85fa1b9d19beca6bd879d98bc7a24af0fd5756c5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47510491"
---
# <a name="configuration-options-overview"></a>Übersicht über Konfigurationsoptionen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Übersicht über Konfigurationsoptionen](https://docs.microsoft.com/visualstudio/extensibility/internals/configuration-options-overview).  
  
Projekte in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] unterstützen mehrere Konfigurationen, die debuggten, ausführen und/oder bereitgestellten erstellt werden können. Eine Konfiguration ist ein Build mit einer benannten Menge von Eigenschaften, in der Regel Compilerschalter und Dateispeicherorte beschrieben. Neue Lösungen enthalten standardmäßig zwei Konfigurationen, Debug und Release. Diese Konfigurationen können angewendet werden, verwenden die Standardeinstellungen, oder geändert, um spezifische Lösung und/oder Anforderungen zu erfüllen. Einige Pakete können auf zwei Arten erstellt werden: als ActiveX-Editor oder als eine Komponente des direktes. Projekte müssen nicht mehrere Konfigurationen, jedoch zu unterstützen. Wenn nur eine Konfiguration vorhanden ist, wird die Konfiguration aller Projektmappenkonfigurationen zugeordnet.  
  
 Konfigurationen in der Regel besteht aus zwei Teilen – den Namen (z. B. Debug oder Release) und die Einstellungen der Plattform. Ein Konfigurationsname Plattform identifiziert, die Umgebung, die die Konfiguration ausgerichtet ist, z. B. eine API festlegen oder die Plattform des Betriebssystems. Benutzer von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] eine Plattform; kann nicht erstellt werden aus der Auswahl müssen sie ein Projekt ermöglicht das VSPackage auswählen. Wenn ein Benutzer installiert ein VSPackage, die Delivery-Plattform, die während der Entwicklung des Pakets erstellt alle gewünschten Plattformname auftreten kann Basis auf von Kriterien festlegen, durch den Paketersteller. Der Benutzer kann dann auswählen, aus der Liste der Plattformen, die über das VSPackage verfügbar gemacht, wenn die Eigenschaftenseiten instanziiert werden.  
  
 Plattformnamen sind optional, da nicht alle Projekte das Konzept der Plattformen unterstützt. Wenn eine Konfiguration nicht über einen Plattformnamen verfügt, wird die Zeichenfolge "n/v" in der Benutzeroberfläche angezeigt.  
  
 Jede Lösung verfügt über einen eigenen Satz von Konfigurationen, die nur zu einem Zeitpunkt aktiv sein kann. Eine Projektmappenkonfiguration ist eine Reihe von nicht mehr als eine Konfiguration aus dem Projekt. Die Bedingung ist "nicht mehr als" ist aufgrund der Option, eine Konfiguration der Projektmappe ein Projekt ausgeschlossen werden sollen. Benutzer können eigene benutzerdefinierte Projektmappenkonfigurationen erstellen.  
  
 Die folgende Tabelle zeigt die typischen Konfigurationen Einrichtung für ein Projekt. Die Zeilen werden mit dem Konfigurationsnamen und die Spalten mit Plattformnamen bezeichnet.  
  
|Konfigurationsname|Plattform: Win32|Plattform: Win64|  
|------------------------|----------------------|----------------------|  
|Debug|\<Debug-Win32-Einstellungen >|\<Debug-Win64-Einstellungen >|  
|Release|\<Einstellungen für die Win32-Version >|\<Releaseeinstellungen Win64 >|  
|MyConfig|Nicht zutreffend|\<MyConfig Win64-Einstellungen >|  
  
> [!NOTE]
>  Sie können keine Projektmappenkonfiguration "MyConfig" erstellen, die eine Plattform für die "Win32" ausschließt, es sei denn, das Projekt, die, das Sie Anzielen, Win32 nicht unterstützt.  
  
 Ändern die aktive Konfiguration für eine Lösung wählt den Satz von Projektkonfigurationen, die erstellt, ausführen, Debuggen oder bereitgestellt werden, in dieser Lösung. Wenn Sie die aktive Projektmappenkonfiguration aus Release in Debug ändern, werden in der Projektmappe alle Projekte z. B. automatisch mit der Projekte Konfiguration angegeben, in der Projektmappe-Debug-Konfiguration erstellt. Die Projekte-Konfigurationen sind in der Regel auch benannte Debuggen, wenn der Benutzer die manuelle Änderungen im Konfigurations-Manager der Umgebung vorgenommen hat.  
  
 Für jedes Projekt gespeicherten Eigenschaften der Projektmappe enthalten den Projektnamen, Projektkonfigurationsname, Flags an, ob zum Erstellen oder zum Bereitstellen und der Name der Projektmappenplattform auf. Weitere Informationen finden Sie unter [Projektmappenkonfiguration](../../extensibility/internals/solution-configuration.md).  
  
 Der Benutzer kann anzeigen und Festlegen von Konfigurationsparametern durch Auswählen der Lösung in der Hierarchie (Projektmappen-Explorer), und öffnen die Eigenschaftenseiten für Projektmappen. Auf ähnliche Weise können Sie anzeigen und ändern Konfigurationsparameter Projekt, wählen Sie im Projektmappen-Explorer das Projekt, und öffnen die Eigenschaftenseiten für das betreffende Projekt.  
  
 Benutzer kann auch ein Projekt mit Einstellungen für Releasekonfiguration und die übrigen Einstellungen für Debugkonfiguration bei Bedarf erstellen. Weitere Informationen finden Sie unter [Projektkonfiguration für das Erstellen von](../../extensibility/internals/project-configuration-for-building.md).  
  
 Das folgende Diagramm zeigt, wie die Schnittstellen, die Unterstützung von Projektmappen- und Projektkonfigurationen implementiert werden:  
  
 ![Grafik zu Konfigurationsschnittstellen](../../extensibility/internals/media/vsconfiginterfaces.gif "VsConfigInterfaces")  
Konfigurationsschnittstellen  
  
 Einige Hinweise, die im Zusammenhang mit der vorherigen Abbildung:  
  
-   `IDispatch` wird in der Configuration-Objekt als optional gekennzeichnet. Es handelt sich hierbei optional, um die Konfigurationsschnittstellen auf dem Suchobjekt haben.  
  
-   `IVsDebuggableProjectCfg` wird in das Konfigurationsobjekt optional gekennzeichnet, aber für die Debugunterstützung erforderlich ist.  
  
-   `IVsProjectCfg2` wird in das Konfigurationsobjekt optional gekennzeichnet, aber ist erforderlich, für die Ausgabe, die Unterstützung zu gruppieren.  
  
-   Die `Config Provider` Objekt als ein optionales Objekt markiert ist, aber die Option ist, wo es implementiert. Sie können das Objekt auf das Projektobjekt oder auf ein separates Objekt implementiert.  
  
-   `IVsCfgProvider2` für die Plattform-Unterstützung und Bearbeitung ist erforderlich. `IVsCfgProvider` ist ausreichend, wenn Sie nicht diese Funktion implementieren.  
  
-   Einige dieser Objekte, die im Diagramm angezeigt werden, als separate Objekte ggf. zu derselben Klasse kombiniert werden können je nach bestimmten Designs. In anderen Themen in diesem Abschnitt werden jedoch die Objekte und Schnittstellen, die mit diesen Objekten verknüpft ist gemäß dem Szenario, in der Abbildung dargestellten erläutert.  
  
-   Bestimmte Objekte werden separat implementiert. Z. B. auftreten, Projekt- und Projektmappen erstellen von separaten Threads und dem Objekt um die Arbeit mit Build getrennt aus dem Objekt beschreiben die Konfiguration für den Build zu verwalten.  
  
 Weitere Informationen auf dem Konfigurationsobjekt Schnittstellen und Konfigurationsanbieterobjekt Schnittstellen in der vorherigen Abbildung finden Sie unter [Projektkonfigurationsobjekt](../../extensibility/internals/project-configuration-object.md). Darüber hinaus [Projektkonfiguration für das Erstellen von](../../extensibility/internals/project-configuration-for-building.md) enthält weitere Informationen zu den Schnittstellen Konfigurations-Generator und Erstellen der Dependency-Objekt, und [Projektkonfiguration für die Verwaltung von Bereitstellung](../../extensibility/internals/project-configuration-for-managing-deployment.md) Weitere beschreibt die Schnittstellen, die an die die Konfiguration Bereitsteller oder Abhängigkeitsobjekte, die Bereitstellung ein. Zum Schluss [Projektkonfiguration für die Ausgabe](../../extensibility/internals/project-configuration-for-output.md) beschreibt die Ausgabegruppe und Ausgabeobjekt-Schnittstellen und die Verwendung von Eigenschaftenseiten, um die konfigurationsabhängigen Eigenschaften anzuzeigen und festzulegen.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>   
 [Konfiguration für die Erstellung des Projekts](../../extensibility/internals/project-configuration-for-building.md)   
 [Projektmappenkonfiguration](../../extensibility/internals/solution-configuration.md)

