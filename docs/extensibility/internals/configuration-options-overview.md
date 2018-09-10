---
title: Übersicht der Konfigurationsoptionen | Microsoft-Dokumentation
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
ms.openlocfilehash: 60f73089c2894bd04c877302e87f11b77928048e
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2018
ms.locfileid: "39510352"
---
# <a name="configuration-options-overview"></a>Übersicht über Konfigurationsoptionen
Projekte in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] unterstützen mehrere Konfigurationen, die debuggten, ausführen und/oder bereitgestellten erstellt werden können. Eine Konfiguration ist ein Build mit einer benannten Menge von Eigenschaften, in der Regel Compilerschalter und Dateispeicherorte beschrieben. Neue Lösungen enthalten standardmäßig zwei Konfigurationen *Debuggen* und *Version*. Diese Konfigurationen können angewendet werden, verwenden die Standardeinstellungen, oder geändert, um spezifische Lösung und/oder Anforderungen zu erfüllen. Einige Pakete können auf zwei Arten erstellt werden: als ActiveX-Editor oder als eine Komponente des direktes. Projekte müssen nicht mehrere Konfigurationen, jedoch zu unterstützen. Wenn nur eine Konfiguration vorhanden ist, wird die Konfiguration aller Projektmappenkonfigurationen zugeordnet.  
  
 Konfigurationen in der Regel besteht aus zwei Teilen: der Name der Konfiguration (wie z. B. *Debuggen* oder *Version*) und die plattformeinstellungen für die. Ein Konfigurationsname Plattform identifiziert, die Umgebung, die die Konfiguration ausgerichtet ist, z. B. eine API festlegen oder die Plattform des Betriebssystems. Benutzer von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] eine Plattform; kann nicht erstellt werden aus der Auswahl müssen sie ein Projekt ermöglicht das VSPackage auswählen. Wenn ein Benutzer installiert ein VSPackage, die Delivery-Plattform, die während der Entwicklung des Pakets erstellt alle gewünschten Plattformname auftreten kann Basis auf von Kriterien festlegen, durch den Paketersteller. Der Benutzer kann dann auswählen, aus der Liste der Plattformen, die über das VSPackage verfügbar gemacht, wenn die Eigenschaftenseiten instanziiert werden.  
  
 Plattformnamen sind optional, da nicht alle Projekte das Konzept der Plattformen unterstützt. Wenn eine Konfiguration verfügt nicht über einen Plattformnamen, die Zeichenfolge **n/v** in der Benutzeroberfläche angezeigt wird.  
  
 Jede Lösung verfügt über einen eigenen Satz von Konfigurationen, die nur zu einem Zeitpunkt aktiv sein kann. Eine Projektmappenkonfiguration ist eine Reihe von nicht mehr als eine Konfiguration aus dem Projekt. Die Bedingung ist "nicht mehr als" ist aufgrund der Option, eine Konfiguration der Projektmappe ein Projekt ausgeschlossen werden sollen. Benutzer können eigene benutzerdefinierte Projektmappenkonfigurationen erstellen.  
  
 Die folgende Tabelle zeigt die typischen Konfigurationen Einrichtung für ein Projekt. Die Zeilen werden mit dem Konfigurationsnamen und die Spalten mit Plattformnamen bezeichnet.  
  
|Konfigurationsname|Plattform: Win32|Plattform: Win64|  
|------------------------|----------------------|----------------------|  
|*Debuggen*|\<Debug-Win32-Einstellungen >|\<Debug-Win64-Einstellungen >|  
|*Version*|\<Einstellungen für die Win32-Version >|\<Releaseeinstellungen Win64 >|  
|*MyConfig*|Nicht zutreffend|\<MyConfig Win64-Einstellungen >|  
  
> [!NOTE]
>  Sie können nicht erstellt werden ein *MyConfig* Projektmappenkonfiguration, die von einer Win32-Plattform werden ausgeschlossen, es sei denn, Sie für das Projekt entwickeln Win32 nicht unterstützt.  
  
 Wählt aus den Satz von Projektkonfigurationen, die erstellt, ausführen, Debuggen oder bereitgestellt wird, ändern die aktive Konfiguration für eine Lösung in dieser Lösung. Angenommen, Sie ändern, dass die aktive Projektmappenkonfiguration aus *Version* zu *Debuggen*, in der Projektmappe alle Projekte werden automatisch erstellt, mit der Projekte Konfiguration angegeben, der Debug-Konfiguration der Lösung. Die Projekte-Konfigurationen werden auch als *Debuggen* , wenn der Benutzer die manuelle Änderungen im Konfigurations-Manager der Umgebung vorgenommen hat.  
  
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
  
-   Der Konfigurationsanbieter-Objekt als ein optionales Objekt markiert ist, aber die Option ist, wo es implementiert. Sie können das Objekt auf das Projektobjekt oder auf ein separates Objekt implementiert.  
  
-   `IVsCfgProvider2` für die Plattform-Unterstützung und Bearbeitung ist erforderlich. `IVsCfgProvider` ist ausreichend, wenn Sie nicht diese Funktion implementieren.  
  
-   Einige dieser Objekte, die im Diagramm angezeigt werden, als separate Objekte ggf. zu derselben Klasse kombiniert werden können je nach bestimmten Designs. In anderen Themen in diesem Abschnitt werden jedoch die Objekte und Schnittstellen, die mit diesen Objekten verknüpft ist gemäß dem Szenario, in der Abbildung dargestellten erläutert.  
  
-   Bestimmte Objekte werden separat implementiert. Z. B. auftreten, Projekt- und Projektmappen erstellen von separaten Threads und dem Objekt um die Arbeit mit Build getrennt aus dem Objekt beschreiben die Konfiguration für den Build zu verwalten.  
  
 Weitere Informationen zu den Configuration-Schnittstellen und Konfigurationsschnittstellen Anbieter-Objekt in der vorherigen Abbildung, finden Sie unter [projektkonfigurationsobjekt](../../extensibility/internals/project-configuration-object.md). Darüber hinaus [Projektkonfiguration für das Erstellen von](../../extensibility/internals/project-configuration-for-building.md) finden Sie weitere Informationen von der Konfigurations-Generator und Build-Abhängigkeit-Schnittstellen, und [Projektkonfiguration für die Verwaltung der Bereitstellung](../../extensibility/internals/project-configuration-for-managing-deployment.md) Weitere beschreibt die Schnittstellen, die an die die Konfiguration Bereitsteller oder Abhängigkeitsobjekte, die Bereitstellung ein. Zum Schluss [Projektkonfiguration für die Ausgabe](../../extensibility/internals/project-configuration-for-output.md) beschreibt Ausgabegruppe und Ausgabe-Schnittstellen und die Verwendung von Eigenschaftenseiten zum konfigurationsabhängigen Eigenschaften anzuzeigen und festzulegen.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>   
 [Konfiguration für die Erstellung des Projekts](../../extensibility/internals/project-configuration-for-building.md)   
 [Projektmappenkonfiguration](../../extensibility/internals/solution-configuration.md)