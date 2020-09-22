---
title: VSIX-Projektvorlage | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- deploy packages
- publish extension
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2386f1be805f6347fc32fba4ee8bfe57c8602329
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841235"
---
# <a name="vsix-project-template"></a>VSIX-Projektvorlage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die VSIX-Projektvorlage verwenden, um eine oder mehrere Visual Studio-Erweiterungen in ein VSIX-Projekt einzubinden und das Paket dann auf der [Visual Studio Marketplace](https://marketplace.visualstudio.com/) -Website zu veröffentlichen.  
  
 VSIX-Bereitstellung unterstützt VSPackages, Assemblys, MEF-Komponenten, Projektvorlagen, Element Vorlagen, Toolbox-Steuerelemente und benutzerdefinierte Erweiterungs Typen.  
  
> [!NOTE]
> Um VSIX-Projekte verwenden zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen zum Visual Studio SDK finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="where-to-find-the-vsix-project-template"></a>Suchen der VSIX-Projektvorlage  
 Die VSIX-Projektvorlage steht im Dialogfeld **Neues Projekt** zur Verfügung. Erweitern Sie entweder den Knoten **Visual Basic** oder den Knoten **Visual c#** , und wählen Sie dann **Erweiterbarkeit**aus.  
  
> [!TIP]
> Stellen Sie sicher, dass in der Dropdown Liste oben im Dialogfeld **Neues Projekt** .NET Framework 4,5 oder höher angegeben ist.  
  
## <a name="uses-of-the-vsix-project-template"></a>Verwendung der VSIX-Projektvorlage  
 Die VSIX-Projektvorlage hat zwei Haupt Verwendungsmöglichkeiten:  
  
- Zum Bereitstellen von Projektvorlagen, Element Vorlagen und anderen Erweiterungen, die noch nicht über VSIX-Unterstützung verfügen.  
  
- Zum Einschließen der Ausgaben mehrerer Erweiterungen in ein Bereitstellungs Paket.  
  
  Sie müssen nicht die VSIX-Projektvorlage verwenden, um VSPackages oder andere Arten von Erweiterungen bereitzustellen, die bereits über VSIX-Unterstützung verfügen.  
  
## <a name="packaging-an-extension-in-an-empty-vsix-project"></a>Verpacken einer Erweiterung in einem leeren VSIX-Projekt  
 Sie können eine vorhandene Erweiterung oder eine Erweiterung, die noch nicht über VSIX-Unterstützung verfügt, packen, indem Sie Sie in ein leeres VSIX-Projekt umschließt. Die zu umschließende Erweiterung muss von einem Typ sein, der vom [VSIX-Schema](../extensibility/vsix-extension-schema-2-0-reference.md)unterstützt wird.  
  
#### <a name="to-package-an-extension-by-using-a-vsix-project"></a>So packen Sie eine Erweiterung mithilfe eines VSIX-Projekts  
  
1. Erstellen Sie die Projekte, die ihre Erweiterung bilden.  
  
2. Erstellen Sie ein VSIX-Projekt mithilfe der **VSIX-Projekt** Vorlage.  
  
     "Source. Extension. vsixmanifest" wird im **Manifest-Designer**geöffnet.  
  
3. Wählen Sie auf der Registerkarte **Objekte** die Schaltfläche **neu** aus.  
  
     Das Dialogfeld **Neues Objekt hinzufügen** wird angezeigt.  
  
4. Wählen Sie in der Liste **Typ** den Typ der Erweiterung aus, die Sie hinzufügen möchten.  
  
5. Führen Sie die folgenden Schritte aus, um eine Erweiterung oder ein Inhalts Element hinzuzufügen, das in der aktuellen Projekt Mappe enthalten ist (z. b. eine Element Vorlage oder eine kompilierte Assembly):  
  
    1. Wählen Sie **Source** in der Liste Quelle **ein Projekt in der aktuellen Projekt**Mappe aus.  
  
    2. Wählen Sie in der Liste **Projekt** den Namen der Erweiterung aus.  
  
    3. Geben Sie im Feld **in diesen Ordner einbetten** den Namen eines Ordners ein, in den das Medienobjekt eingebettet werden soll, und klicken Sie dann auf die Schaltfläche **OK** .  
  
6. Führen Sie die folgenden Schritte aus, um eine Erweiterung oder ein Inhalts Element hinzuzufügen, die nicht in der aktuellen Projekt Mappe enthalten ist:  
  
    1. Wählen Sie im Listenfeld **Quelle** die Option **Datei im Dateisystem**aus.  
  
    2. Geben Sie im Feld **Pfad** den vollständigen Pfad zur kompilierten oder komprimierten Erweiterungs Datei ein, oder verwenden Sie die Schaltfläche **Durchsuchen** , um zu der Datei zu navigieren.  
  
    3. Geben Sie im Feld **in diesen Ordner einbetten** den Namen eines Ordners ein, in den das Medienobjekt eingebettet werden soll, und klicken Sie dann auf die Schaltfläche **OK** .  
  
7. Wenn Sie möchten, dass das Paket zusätzliche Erweiterungen enthält, fügen Sie diese auf die gleiche Weise hinzu.  
  
8. Erstellen Sie die Projektmappe.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] erstellt eine VSIX-Datei, die eine VSIX-Manifest-Datei, eine [Content_Types]. XML-Datei und alle Erweiterungs Ressourcen enthält, die Sie dem Projekt hinzugefügt haben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [VSIX-Erweiterungs Schema 2,0-Referenz](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [Suchen und Verwenden von Visual Studio-Erweiterungen](../ide/finding-and-using-visual-studio-extensions.md)
