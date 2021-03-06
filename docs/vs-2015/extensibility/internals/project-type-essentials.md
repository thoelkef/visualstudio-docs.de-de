---
title: Projekttyp Essentials | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7e45d5f252deaf1788ae5093048ef8afb900fbe4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704065"
---
# <a name="project-type-essentials"></a>Grundlagen zu Projekttypen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] umfasst mehrere Projekttypen für Sprachen, wie [!INCLUDE[csprcs](../../includes/csprcs-md.md)] z [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] . b. oder. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] mit können Sie auch eigene Projekttypen erstellen.  
  
 Wenn Sie nur benutzerdefinierte Befehle, Editoren oder Tool Fenster hinzufügen möchten [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , können Sie dies tun, ohne einen neuen Projekttyp erstellen zu müssen. Weitere Informationen finden Sie unter den folgenden Themen:  
  
- [Befehle, Menüs und Symbolleisten](../../extensibility/internals/commands-menus-and-toolbars.md)  
  
- [Editor- und Sprachdiensterweiterungen](../../extensibility/editor-and-language-service-extensions.md)  
  
- [Erweitern und Anpassen von Toolfenstern](../../extensibility/extending-and-customizing-tool-windows.md)  
  
  Wenn Sie das Verhalten der angegebenen [!INCLUDE[csprcs](../../includes/csprcs-md.md)] -und-Projekttypen anpassen möchten [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] , können Sie dies auch mithilfe von Projekt Untertypen tun. Weitere Informationen finden Sie unter [Projekt Untertypen](../../extensibility/internals/project-subtypes.md).  
  
  Für Projekte, die auf einer anderen Sprache als basieren, müssen Sie einen neuen [!INCLUDE[csprcs](../../includes/csprcs-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] Projekttyp erstellen, wenn Sie eine oder mehrere der folgenden Aktionen unterstützen möchten:  
  
- Entwickeln  
  
- Bereitstellung  
  
- Mehrere Konfigurationen  
  
- Quellcodeverwaltung  
  
- Debuggen  
  
- Projekt Elemente in Projektmappen-Explorer  
  
- Die Dialogfelder " **Projekt öffnen** " oder " **Neues Projekt** "  
  
- Projekt Schachtelung  
  
- Weitere Informationen zu den Funktionen von Projekttypen finden Sie in den folgenden Bereichen:  
  
- Projekttypen sind Objekte in einem VSPackage, die den Satz von erwarteten Schnittstellen implementieren [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Wenn Sie c# verwenden, um einen Projekttyp zu entwickeln, implementieren die Projektklassen des Managed Package Frameworks die erforderlichen Schnittstellen für Sie, und Sie können diese Implementierung erben. Weitere Informationen finden Sie unter [Verwenden des Managed Package Frameworks zum Implementieren eines Projekt Typs (c#)](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md).  
  
- Für C++-Entwickler funktionieren die Klassen in der Hierarchien-Bibliothek auf ähnliche Weise. Weitere Informationen finden Sie unter [nicht im Build: Verwenden von HierUtil7-Projektklassen zum Implementieren eines Projekt Typs (C++)](https://msdn.microsoft.com/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
- Projekttypen können andere Daten als typische Quell Code Dateien unterstützen, die in einer exe-oder dll-Assembly erstellt werden. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Datenbankprojekte enthalten z. b. Verweise auf Skript-und Abfrage Dateien, die auf dem Datenträger gespeichert sind, und fügen Befehle zu **Projektmappen-Explorer** hinzu, um die Skripts und Abfragen für eine Datenbank auszuführen, aber die Projekte unterstützen kein Buildverhalten Weitere Informationen finden Sie unter [Öffnen und Speichern von Projekt Elementen](../../extensibility/internals/opening-and-saving-project-items.md).  
  
- Bei einem Projekttyp müssen überhaupt keine Dateien verwendet werden. Ein Projekttyp könnte z. b. alle zugehörigen Daten in einer Datenbank speichern. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] gibt Projekttypen die Kontrolle darüber, wie Sie Daten für Projekte und Projekt Elemente beibehalten. Weitere Informationen finden Sie unter [Entwurfsentscheidungen für Projekttyp](../../extensibility/internals/project-type-design-decisions.md).  
  
- Projekttypen müssen eine *projektfactory*bereitstellen, bei der es sich um ein Objekt handelt, das eine Instanz des Projekt Typs erstellt, wenn [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ein Projekt, das auf diesem Projekttyp basiert, geöffnet oder erstellt werden soll. Weitere Informationen finden Sie unter [Erstellen von Projekt Instanzen mithilfe von projektfactorys](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
- Projekttypen müssen Vorlagen für Projekte und Projekt Elemente bereitstellen. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] verwendet die Vorlagen, wenn Benutzer neue Projekte erstellen und vorhandenen Projekten neue Elemente hinzufügen. Weitere Informationen finden Sie unter [Hinzufügen von Projekt-und Projekt Element Vorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
- Projekttypen können mehrere Konfigurationen unterstützen, z. b. Debug und Release. Benutzer können die verschiedenen Konfigurationen eines Projekts mithilfe der von Ihnen bereitgestellten Eigenschaften Seiten ändern. Weitere Informationen finden Sie unter [Verwalten von Konfigurationsoptionen](../../extensibility/internals/managing-configuration-options.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Bereitstellen von Projekttypen](../../extensibility/internals/deploying-project-types.md)
