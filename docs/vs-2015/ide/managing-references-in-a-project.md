---
title: Verwalten von Verweisen in einem Projekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.ProjectPropertiesReferencePaths
- cs.ProjectPropertiesReferencePaths
helpviewer_keywords:
- Visual C# projects, references
- referencing objects, project references
- external component references
- referencing namespaces
- Visual Basic projects, references
- referencing components, external components
- Web references, types of project references
- namespaces [Visual Studio], referencing
- COM components, referencing
- objects [Visual Studio], referencing
ms.assetid: 05d1c51b-44f3-4973-8a11-6c919b08ad62
caps.latest.revision: 55
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: aa9b96370d6b0e1b39b414eeee737a32bfefcd34
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47523600"
---
# <a name="managing-references-in-a-project"></a>Verwalten von Verweisen in einem Projekt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bevor Sie Code schreiben können, der sich auf eine externe Komponente oder einen verbundenen Dienst bezieht, müssen Sie zunächst einen Verweis auf diese Komponente im Projekt einrichten. Ein Verweis ist im Prinzip ein Eintrag in einer Projektdatei, der Informationen beinhaltet, die von Visual Studio zum Auffinden der Komponente oder des Diensts benötigt.  
  
 Um einen Verweis hinzuzufügen, klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Knoten „Verweise“, und klicken Sie dann auf **Verweis hinzufügen**. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen und Entfernen von Verweisen mit dem Verweis-Manager](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md).  
  
 ![Hinzufügen eines Verweises in Visual C&#43;&#43;](../ide/media/vs2015-cpp-add-reference.png "vs2015_cpp_add_reference")  
  
 Sie können einen Verweis auf die folgenden Komponenten-/Diensttypen erstellen:  
  
-   Verweise auf Windows Store-App  
  
-   .NET Framework-Klassenbibliotheken oder -Assemblys  
  
-   COM-Komponenten  
  
-   Sonstige Assemblys oder Klassenbibliotheken von Projekten in derselben Projektmappe  
  
-   XML-Webdienste  
  
## <a name="windows-store-app-references"></a>Verweise auf Windows Store-App  
  
### <a name="project-references"></a>Projektverweise  
 Projekte der universellen Windows-Plattform (UWP), die auf Windows 10 ausgerichtet sind, können in der Projektmappe Verweise auf andere UWP-Projekte oder auf Windows Store-Projekte bzw. auf Binärdateien für [!INCLUDE[win81](../includes/win81-md.md)] erstellen. Voraussetzung hierfür ist, dass diese Projekte keine APIs verwenden, die in Windows 10 nicht mehr verwendet werden. Weitere Informationen finden Sie unter [Move from Windows Runtime 8 to UWP](https://msdn.microsoft.com/library/windows/apps/dn954974.aspx)(Von Windows-Laufzeit zu UWP) (möglicherweise in englischer Sprache).  
  
 Informationen zur Neuausrichtung der [!INCLUDE[win81](../includes/win81-md.md)]-Projekte auf Windows 10 finden Sie unter [Portieren, Migrieren und Aktualisieren von Visual Studio-Projekten](../porting/porting-migrating-and-upgrading-visual-studio-projects.md).  
  
### <a name="extension-sdk-references"></a>Verweise auf das Erweiterungs-SDK  
 Visual Basic-, C#-, C++- und JavaScript-Windows Store-Projekte, die auf UWP (Universal Windows Platform) abzielen, können auf Erweiterungs-SDKs verweisen, die auf [!INCLUDE[win81](../includes/win81-md.md)] ausgerichtet sind, sofern diese Erweiterungs-SDKs keine APIs verwenden, die in Windows 10 als veraltet gelten. Überprüfen Sie die Website des Anbieters des Erweiterungs-SDKs, um festzustellen, ob Windows Store-Projekte, die auf UWP abzielen, auf das SKD verweisen können.  
  
 Wenn Sie feststellen, dass das Erweiterungs-SDK, auf das von Ihrer Anwendung verwiesen wird, nicht unterstützt wird, müssen Sie folgende Schritte ausführen:  
  
1.  Schauen Sie sich den Namen des Projekts an, das den Fehler verursacht. Die Plattform, auf die Ihr Projekt abzielt, steht in Klammern neben dem Projektnamen. Beispielsweise bedeutet **MyProjectName (Windows 8.1)**, dass das Projekt **MyProjectName** auf die Plattformversion [!INCLUDE[win81](../includes/win81-md.md)]abzielt.  
  
2.  Wechseln Sie zur Website des Anbieters des nicht unterstützten Erweiterungs-SDKs, und installieren Sie die Version des Erweiterungs-SDKs mit Abhängigkeiten, die mit der Version der Plattform kompatibel sind, auf die Ihr Projekt abzielt.  
  
    > [!NOTE]
    >  Eine Möglichkeit, um herauszufinden, ob das zuvor installierte Erweiterungs-SDK Abhängigkeiten von anderen Erweiterungs-SDKs aufweist, besteht darin, Visual Studio neu zu starten. Erstellen Sie dann ein neues C#-Windows Store-Projekt, klicken Sie mit der rechten Maustaste auf das Projekt, und wählen Sie **Verweis hinzufügen**, wechseln Sie zur Registerkarte **Windows** , wechseln Sie zur Unterregisterkarte **Erweiterungen** , wählen Sie das Erweiterungs-SDK aus, und schauen Sie sich den rechten Bereich des **Verweis-Managers**an. Wenn Abhängigkeiten bestehen, werden sie dort aufgeführt.  
  
    > [!IMPORTANT]
    >  Wenn Ihr Projekt auf Windows 10 abzielt und das im vorherigen Schritt installierte Erweiterungs-SDK von Microsoft Visual C++ Runtime Package abhängt, lautet die Version von Microsoft Visual C++ Runtime Package, die mit Windows 10 kompatibel ist, v14.0 und wird mit Visual Studio 2015 installiert.  
  
3.  Wenn das im vorherigen Schritt installierte Erweiterungs-SDK von anderen Erweiterungs-SDKs abhängt, rufen Sie die Websites der entsprechenden Anbieter auf, und installieren Sie die Versionen, die mit der Version der Plattform kompatibel sind, auf die Ihr Projekt abzielt.  
  
4.  Starten Sie Visual Studio neu, und öffnen Sie Ihre App.  
  
5.  Klicken Sie im Projekt, das den Fehler verursacht hat, mit der rechten Maustaste auf den Knoten **Verweise** , und wählen Sie **Verweis hinzufügen**  
  
6.  Klicken Sie auf die Registerkarte **Fenster** und anschließend auf die Unterregisterkarte **Erweiterungen** . Deaktivieren Sie dann die Kontrollkästchen für die alten Erweiterungs-SDKs, und aktivieren Sie die Kontrollkästchen für die neuen Erweiterungs-SDKs. Klicken Sie auf **OK**.  
  
## <a name="adding-a-reference-at-design-time"></a>Hinzufügen von Verweisen zur Entwurfszeit  
 Wenn Sie einen Verweis auf eine Assembly im Projekt erstellen, verwendet [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] für die Suche der Assembly die folgenden Speicherorte:  
  
-   Das aktuelle Projektverzeichnis. (Sie können die Assemblys über die Registerkarte **Durchsuchen** suchen.)  
  
-   Andere Projektverzeichnisse in der gleichen Projektmappe. (Sie finden diese Assemblys auf der Registerkarte **Projekte** .)  
  
> [!NOTE]
>  Alle Projekte enthalten einen impliziten Verweis auf "mscorlib". Visual Basic-Projekte enthalten einen impliziten Verweis auf `Microsoft.VisualBasic`.  
>   
>  Alle Projekte in Visual Studio 2010 enthalten einen impliziten Verweis auf `System.Core`. Dies gilt auch, wenn `System.Core` aus der Liste der Verweise entfernt wird.  
  
## <a name="references-to-shared-components-at-run-time"></a>Verweise auf freigegebene Komponenten zur Laufzeit  
 Zur Laufzeit müssen Komponenten werden entweder im Ausgabepfad des Projekts oder in der [Global Assembly Cache](http://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202) (GAC). Wenn das Projekt einen Verweis auf ein Objekt enthält, der sich nicht an einem dieser Orte befindet, müssen Sie den Verweis beim Erstellen des Projekts in den Ausgabepfad des Projekts kopieren. Die <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> -Eigenschaft gibt an, ob diese Kopie erstellt werden muss. Wenn der Wert **True**lautet, wird der Verweis beim Erstellen des Projekts in das Projektverzeichnis kopiert. Wenn der Wert **False**ist, wird der Verweis nicht kopiert.  
  
 Wenn Sie eine Anwendung bereitstellen, die einen Verweis auf eine im GAC registrierte benutzerdefinierte Komponente enthält, wird die Komponente unabhängig von der <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> -Einstellung nicht mit der Anwendung bereitgestellt. In früheren Versionen von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] konnten Sie die <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A>-Eigenschaft für einen Verweis festlegen, um sicherzustellen, dass die Assembly bereitgestellt wird. Jetzt müssen Sie die Assembly manuell dem Ordner \Bin hinzufügen. Dadurch wird der gesamte benutzerdefinierte Code einer Prüfung unterzogen, und das Risiko der Veröffentlichung von unbekanntem benutzerdefinierten Code wird vermindert.  
  
 Wenn sich die Assembly bzw. Komponente im globalen Assemblycache befindet oder eine .NET Framework-Komponente ist, wird die <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> -Eigenschaft standardmäßig auf **False** festgelegt. Andernfalls wird der Wert auf **True**festgelegt. Verweise zwischen Projekten werden immer auf **True**festgelegt.  
  
## <a name="referencing-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>Verweisen auf ein Projekt oder eine Assembly, die auf eine andere Version von .NET Framework abzielt  
 Sie können Anwendungen erstellen, die auf Projekte oder Assemblys verweisen, die auf eine andere Version von .NET Framework abzielen. Sie können z. B. eine Anwendung erstellen, die auf [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)] abzielt, das auf eine Assembly verweist, die wiederum auf [!INCLUDE[dnprdnext](../includes/dnprdnext-md.md)] abzielt. Wenn Sie ein Projekt erstellen, das auf eine frühere Version von [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] abzielt, können Sie keinen Verweis in diesem Projekt auf ein Projekt oder eine Assembly festlegen, die auf [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)] oder .NET Framework Version 4 abzielt.  
  
 Weitere Informationen finden Sie unter [Festlegen einer bestimmten .NET-Framework-Zielversion](../ide/targeting-a-specific-dotnet-framework-version.md).  
  
## <a name="project-to-project-references"></a>Projekt-zu-Projekt-Verweise  
 Verweise zwischen Projekten sind Verweise auf Projekte mit Assemblys, die Sie im Dialogfeld **Projekt** erstellen. Visual Studio kann anhand eines Pfads zum Projekt nach einer Assembly suchen.  
  
 Wenn Sie ein Projekt haben, das eine Assembly erstellt, müssen Sie auf das Projekt verweisen und keinen Dateiverweis verwenden (siehe unten). Der Vorteil eines Verweises zwischen Projekten liegt darin, dass eine Abhängigkeit zwischen den Projekten im Buildsystem erzeugt wird. Das abhängige Projekt wird erstellt, wenn es sich seit der letzten Erstellung des verweisenden Projekts geändert hat. Bei Dateiverweisen wird keine Buildabhängigkeit erstellt, d. h., das verweisende Projekt kann ohne Erstellen des abhänigen Projekts erstellt werden, und der Verweis kann veraltet sein. (Das heißt, das Projekt kann auf eine vorher erstellte Version des Projekts verweisen.) Dies kann dazu führen, dass im BIN-Verzeichnis mehrere Versionen einer einzigen DLL erforderlich sind, was jedoch nicht möglich ist. Wenn dieser Konflikt auftritt, wird eine Meldung wie die folgende angezeigt: [Fehler: Die Abhängigkeit „Datei“ in Projekt „Projekt“ kann nicht in das Ausführungsverzeichnis kopiert werden, da sie den Verweis „Datei“ überschreiben würde](../misc/warning-the-dependency-file-in-project-project-cannot-be-copied-to-the-run-directory-because-it-would-overwrite-the-reference-file.md). Weitere Informationen finden Sie unter [Troubleshooting Broken References](../ide/troubleshooting-broken-references.md) und [How to: Create and Remove Project Dependencies](../ide/how-to-create-and-remove-project-dependencies.md).  
  
> [!NOTE]
>  Anstelle eines Projekt-zu-Projekt-Verweises wird ein Dateiverweis erstellt, wenn die Zielversion von .NET Framework eines Projekts Version 4.5 ist und die Zielversion des anderen Projekts Version 2, 3, 3.5 oder 4.0 ist.  
  
## <a name="file-references"></a>Dateiverweise  
 Dateiverweise sind direkte Verweise auf Assemblys außerhalb des Kontexts eines Visual Studio-Projekts. Sie erstellen diese mithilfe der Registerkarte **Durchsuchen** im **Verweis-Manager**. Verwenden Sie einen Dateiverweis, wenn Sie nur eine Assembly oder Komponente haben und nicht über das Projekt verfügen, das dies als Ausgabe erstellt.  
  
## <a name="see-also"></a>Siehe auch  
 [Troubleshooting Broken References](../ide/troubleshooting-broken-references.md)   
 [Programmieren mit Assemblys](http://msdn.microsoft.com/library/25918b15-701d-42c7-95fc-c290d08648d6)   
 [Gewusst wie: Hinzufügen und Entfernen von Verweisen mit dem Verweis-Manager](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md)

