---
title: Grundlagen zu Projekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: caf2b8d75d9c82724474c94fb49fca6b45107d06
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49863567"
---
# <a name="project-type-essentials"></a>Grundlagen zu Projekttypen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] enthält einige Projekttypen für Sprachen wie z. B. [!INCLUDE[csprcs](../../includes/csprcs-md.md)] oder [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Außerdem können Sie eigene Projekttypen zu erstellen.  
  
 Wenn Sie nur benutzerdefinierte Befehle, Editoren oder Toolfenster, hinzufügen möchten [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], können Sie dies tun, ohne dass einen neuer Projekttyp erstellt. Weitere Informationen finden Sie unter den folgenden Themen:  
  
- [Befehle, Menüs und Symbolleisten](../../extensibility/internals/commands-menus-and-toolbars.md)  
  
- [Editor- und Sprachdiensterweiterungen](../../extensibility/editor-and-language-service-extensions.md)  
  
- [Erweitern und Anpassen von Toolfenstern](../../extensibility/extending-and-customizing-tool-windows.md)  
  
  Ebenso sollten Sie das Verhalten des angegebenen anpassen [!INCLUDE[csprcs](../../includes/csprcs-md.md)] und [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] Projekttypen möglich Projektuntertypen verwenden. Weitere Informationen finden Sie unter [Projektuntertypen](../../extensibility/internals/project-subtypes.md).  
  
  Sie müssen einen neuen Projekttyp für Projekte, die nicht auf einer anderen Sprache basieren erstellen [!INCLUDE[csprcs](../../includes/csprcs-md.md)] und [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] sollten Sie eine oder mehrere der folgenden zu unterstützen:  
  
- Build  
  
- Bereitstellung  
  
- Mehrere Konfigurationen  
  
- Quellcodeverwaltung  
  
- Debuggen  
  
- Projektelemente im Projektmappen-Explorer  
  
- Die **geöffneten Projekt** oder **neues Projekt** Dialogfelder  
  
- Projekt Schachtelung  
  
- Weitere Informationen zu den Funktionen der Projekttypen finden Sie hier:  
  
- Projekttypen sind Objekte in einem VSPackage, die den Satz von Schnittstellen implementieren [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] erwartet. Wenn Sie c# verwenden, um einen Projekttyp zu entwickeln, wird die Managed Package Framework-Projekt-Klassen für Sie erforderlichen Schnittstellen zu implementieren und können Sie, dass diese Implementierung erben. Weitere Informationen finden Sie unter [mit dem Managed Package Framework zum Implementieren eines Projekttyps (c#)](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md).  
  
- Arbeiten für C++-Entwickler die Klassen in der Bibliothek HierUtil auf ähnliche Weise. Weitere Informationen finden Sie unter [nicht im Build: Verwenden von HierUtil7 Projektklassen implementieren Sie eine Projekt-Typ (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
- Projekttypen können Daten als typische Quellcodedateien unterstützen, die in eine .exe oder .dll-Assembly zu erstellen. Z. B. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Datenbankprojekte enthalten Verweise auf Dateien, die sich auf Skripts und Abfragen auf dem Datenträger gespeichert und Hinzufügen von Befehlen zum **Projektmappen-Explorer** zum Ausführen der Skripts und Abfragen einer Datenbank, aber die Projekte nicht unterstützen Erstellen Sie Verhalten. Weitere Informationen finden Sie unter [öffnen und Speichern von Projektelementen](../../extensibility/internals/opening-and-saving-project-items.md).  
  
- Ein Projekt muss keine Dateien überhaupt nicht verwenden. Beispielsweise könnte ein Projekttyp sämtlicher Daten in einer Datenbank speichern. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] erhalten Projekttypen vollständig kontrollieren, wie sie Daten für Projekte und Projektelemente erhalten bleiben. Weitere Informationen finden Sie unter [Entwurfsentscheidungen bei Projekttypen](../../extensibility/internals/project-type-design-decisions.md).  
  
- Projekttypen müssen Bereitstellen einer *Projektzuordnungsinstanz*, dies ist ein Objekt, das eine Instanz des Projekts erstellt Geben Sie jedes Mal, wenn [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] wird beim Öffnen oder erstellen ein Projekt, das basierend auf diesen Projekttyp mitgeteilt. Weitere Informationen finden Sie unter [erstellen Projekt Instanzen von mithilfe von Projektfactorys](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
- Projekttypen müssen Vorlagen für Projekte und Projektelemente angeben. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] die Vorlagen verwendet, wenn Benutzer neue Projekte erstellen und neuer Elemente zu vorhandenen Projekten hinzufügen. Weitere Informationen finden Sie unter [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
- Projekttypen können mehrere Konfigurationen, wie Debug und Release unterstützen. Benutzer können mithilfe von Eigenschaftenseiten, mit denen Sie angeben, die verschiedenen Konfigurationen eines Projekts ändern. Weitere Informationen finden Sie unter [Konfigurationsoptionen verwalten](../../extensibility/internals/managing-configuration-options.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Bereitstellen von Projekttypen](../../extensibility/internals/deploying-project-types.md)

