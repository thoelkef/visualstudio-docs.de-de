---
title: Projekttyp Essentials | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 435d3ca0e35911754cac1e37abb276939109a0b3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725406"
---
# <a name="project-type-essentials"></a>Grundlagen zu Projekttypen
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] enthält mehrere Projekttypen für Sprachen wie [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] oder [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] können Sie auch eigene Projekttypen erstellen.

 Wenn Sie nur benutzerdefinierte Befehle, Editoren oder Tool Fenster [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hinzufügen möchten, können Sie dies tun, ohne einen neuen Projekttyp erstellen zu müssen. Weitere Informationen finden Sie unter den folgenden Themen:

- [Befehle, Menüs und Symbolleisten](../../extensibility/internals/commands-menus-and-toolbars.md)

- [Editor- und Sprachdiensterweiterungen](../../extensibility/editor-and-language-service-extensions.md)

- [Erweitern und Anpassen von Toolfenstern](../../extensibility/extending-and-customizing-tool-windows.md)

  Wenn Sie das Verhalten der bereitgestellten [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] und [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Projekttypen anpassen möchten, können Sie dies auch mithilfe von Projekt Untertypen tun. Weitere Informationen finden Sie unter [Projekt Untertypen](../../extensibility/internals/project-subtypes.md).

  Sie müssen einen neuen Projekttyp für Projekte erstellen, die auf einer anderen Sprache als [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] basieren, und [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], wenn Sie eine oder mehrere der folgenden Aktionen unterstützen möchten:

- Build

- Bereitstellung

- Mehrere Konfigurationen

- Quellcodeverwaltung

- Debugging

- Projekt Elemente in Projektmappen-Explorer

- Die Dialogfelder " **Projekt öffnen** " oder " **Neues Projekt** "

- Projekt Schachtelung

- Weitere Informationen zu den Funktionen von Projekttypen finden Sie in den folgenden Bereichen:

- Projekttypen sind Objekte in einem VSPackage, die den Satz von Schnittstellen implementieren, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] erwartet. Wenn Sie verwenden C# , um einen Projekttyp zu entwickeln, implementieren die Projektklassen von Managed Package Framework die erforderlichen Schnittstellen für Sie, und Sie können diese Implementierung erben. Weitere Informationen finden Sie unter [Verwenden des Managed Package Frameworks zum Implementieren eines Projekt TypsC#()](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md).

- Für C++ Entwickler funktionieren die Klassen in der Hierarchien-Bibliothek auf ähnliche Weise. Weitere Informationen finden Sie unter [nicht im Build: Verwenden von HierUtil7-Projektklassen zum Implementieren eines ProjektC++Typs ()](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346).

- Projekttypen können andere Daten als typische Quell Code Dateien unterstützen, die in einer exe-oder dll-Assembly erstellt werden. @No__t_0 Datenbankprojekte z. b. Verweise auf Skript-und Abfrage Dateien enthalten, die auf dem Datenträger gespeichert sind, und **Projektmappen-Explorer** Befehle hinzufügen, um die Skripts und Abfragen für eine Datenbank auszuführen. Weitere Informationen finden Sie unter [Öffnen und Speichern von Projekt Elementen](../../extensibility/internals/opening-and-saving-project-items.md).

- Bei einem Projekttyp müssen überhaupt keine Dateien verwendet werden. Ein Projekttyp könnte z. b. alle zugehörigen Daten in einer Datenbank speichern. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gibt den Projekttypen die Kontrolle darüber, wie Sie Daten für Projekte und Projekt Elemente beibehalten. Weitere Informationen finden Sie unter [Entwurfsentscheidungen für Projekttyp](../../extensibility/internals/project-type-design-decisions.md).

- Projekttypen müssen eine *projektfactory*bereitstellen, bei der es sich um ein Objekt handelt, das eine Instanz des Projekt Typs erstellt, wenn [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] angewiesen wird, ein Projekt zu öffnen oder zu erstellen, das auf diesem Projekttyp basiert. Weitere Informationen finden Sie unter [Erstellen von Projekt Instanzen mithilfe von projektfactorys](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).

- Projekttypen müssen Vorlagen für Projekte und Projekt Elemente bereitstellen. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verwendet die Vorlagen, wenn Benutzer neue Projekte erstellen und vorhandenen Projekten neue Elemente hinzufügen. Weitere Informationen finden Sie unter [Hinzufügen von Projekt-und Projekt Element Vorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md).

- Projekttypen können mehrere Konfigurationen unterstützen, z. b. Debug und Release. Benutzer können die verschiedenen Konfigurationen eines Projekts mithilfe der von Ihnen bereitgestellten Eigenschaften Seiten ändern. Weitere Informationen finden Sie unter [Verwalten von Konfigurationsoptionen](../../extensibility/internals/managing-configuration-options.md).

## <a name="see-also"></a>Siehe auch
- [Bereitstellen von Projekttypen](../../extensibility/internals/deploying-project-types.md)