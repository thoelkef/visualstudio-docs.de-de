---
title: "Projekt Typ Essentials | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Typen [Visual Studio SDK]"
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Projekt Typ Essentials
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] enthält verschiedene Projekttypen für Sprachen wie z. B. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] oder [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Außerdem können Sie eigene Projekttypen erstellen.  
  
 Wenn Sie nur benutzerdefinierte Befehle, Editoren und Toolfenster hinzufügen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], können Sie dies tun, ohne Erstellung eines neuen Projekts. Weitere Informationen finden Sie unter den folgenden Themen:  
  
-   [Befehle, Menüs und Symbolleisten](../../extensibility/internals/commands-menus-and-toolbars.md)  
  
-   [\-Editor, und Language Service Extensions](../../extensibility/editor-and-language-service-extensions.md)  
  
-   [Erweitern und Anpassen von Toolfenstern](../../extensibility/extending-and-customizing-tool-windows.md)  
  
 Ebenso Sie ggf. zum Anpassen des Verhaltens des angegebenen [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] und [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Projekttypen, erreichen Sie mithilfe von Project Untertypen. Weitere Informationen finden Sie unter [Projekt\-Untertypen](../../extensibility/internals/project-subtypes.md).  
  
 Müssen Sie einen neuen Projekttyp für Projekte, die auf einer anderen Sprache als basiert erstellen [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] und [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] wenn Sie eine oder mehrere der folgenden unterstützen möchten:  
  
-   Build  
  
-   Bereitstellung  
  
-   Mehrere Konfigurationen  
  
-   Datenquellen\-Steuerelement  
  
-   Debugging  
  
-   Projektelemente im Projektmappen\-Explorer  
  
-   Die **Öffnen Sie das Projekt** oder **Neues Projekt** Dialogfelder  
  
-   Projekt Schachtelung  
  
-   Weitere Informationen zu den Funktionen der Projekttypen finden Sie unter den folgenden:  
  
-   Projekttypen sind Objekte in einem VSPackage, die Gruppe von Schnittstellen implementieren [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] erwartet. Wenn Sie c\# verwenden, um einen Projekttyp zu entwickeln, Managed Package Framework Projektklassen für Sie erforderlichen Schnittstellen zu implementieren, Sie, dass diese Implementierung übernehmen. Weitere Informationen finden Sie unter [Mithilfe von verwalteten Paketframework implementieren einen Projekttyp \(c\#\)](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md).  
  
-   Für C\+\+\-Entwickler arbeiten die Klassen in der Bibliothek HierUtil auf ähnliche Weise. Weitere Informationen finden Sie unter [nicht im Build: mithilfe von HierUtil7 Projektklassen implementieren eine Projekt\-Typ \(C\+\+\)](http://msdn.microsoft.com/de-de/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
-   Projekttypen unterstützen andere Daten als normale Quellcodedateien, die in eine .exe oder .dll\-Assembly zu erstellen. Z. B. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Datenbankprojekte enthalten Verweise auf Skripts und Abfragen Dateien auf Datenträgern und Hinzufügen von Befehlen zu **Projektmappen\-Explorer** zum Ausführen der Skripts und Abfragen für eine Datenbank, aber die Projekte unterstützen keine Buildverhalten. Weitere Informationen finden Sie unter [Öffnen und Speichern von Projektelementen](../../extensibility/internals/opening-and-saving-project-items.md).  
  
-   Ein Projekttyp muss nicht alle Dateien zu verwenden. Beispielsweise könnte ein Projekttyp alle darin enthaltenen Daten in einer Datenbank speichern.[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Gibt die Projekttypen vollständig steuern, wie sie Daten für Projekte und Projektelemente erhalten bleiben. Weitere Informationen finden Sie unter [Projekt Typ Designentscheidungen](../../extensibility/internals/project-type-design-decisions.md).  
  
-   Projekttypen benötigt eine *Projekt\-Factory*, ist ein Objekt, das eine Instanz des Projekts erstellt geben immer [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] angewiesen, öffnen oder erstellen Sie ein Projekt, das je nach Projekttyp. Weitere Informationen finden Sie unter [Erstellen von Instanzen von Project mithilfe von Project\-Factorys](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
-   Projekttypen müssen Vorlagen für Projekte und Projektelemente angeben.[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] die Vorlagen werden verwendet, wenn Benutzer neue Projekte erstellen und neuer Elemente zu vorhandenen Projekten hinzufügen. Weitere Informationen finden Sie unter [Hinzufügen von Projekt\- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
-   Projekttypen können mehrere Konfigurationen, z. B. Debug\- und unterstützen. Benutzer können die verschiedenen Konfigurationen eines Projekts ändern, durch Verwenden von Eigenschaftenseiten, die Sie angeben. Weitere Informationen finden Sie unter [Verwalten von Konfigurationsoptionen](../../extensibility/internals/managing-configuration-options.md).  
  
## Siehe auch  
 [Bereitstellen von Projekttypen](../../extensibility/internals/deploying-project-types.md)