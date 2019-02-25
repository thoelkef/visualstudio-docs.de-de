---
title: 'Vorgehensweise: Anfügen von Erweiterungen durch verwalteten Code an Dokumente'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], attaching
- documents [Office development in Visual Studio], managed code extensions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c0faac79e99b425eadd4e43c88b0a04dba670731
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56646772"
---
# <a name="how-to-attach-managed-code-extensions-to-documents"></a>Vorgehensweise: Anfügen von Erweiterungen durch verwalteten Code an Dokumente
  Sie können eine Anpassungsassembly an ein vorhandenes Microsoft Office Word-Dokument oder die Microsoft Office Excel-Arbeitsmappe anfügen. Das Dokument oder die Arbeitsmappe kann in einem beliebigen Dateiformat sein, die von der Microsoft Office-Projekten und Entwicklungstools in Visual Studio unterstützt wird. Weitere Informationen finden Sie unter [Architektur von Anpassungen auf Dokumentebene](../vsto/architecture-of-document-level-customizations.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Verwenden Sie zum Anfügen einer Anpassung an ein Word- oder Excel-Dokument die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> Methode der <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Klasse. Da die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Klasse soll auf einem Computer ausgeführt werden, die keine Microsoft Office installiert ist, können Sie diese Methode verwenden, in Projektmappen, die nicht direkt mit Microsoft Office-Entwicklung (z. B. eine Konsole oder Windows Forms-Anwendung) verknüpft sind.

> [!NOTE]
>  Die Anpassung kann nicht geladen werden, wenn der Code Steuerelemente erwartet, die das angegebene Dokument nicht.

 ![Link zum Video](../vsto/media/playvideo.gif "Link zum Video") eine entsprechende Videodemo finden Sie unter [Gewusst wie: Anfügen oder trennen eine VSTO-Assembly aus einem Word-Dokument? ](http://go.microsoft.com/fwlink/?LinkId=136782).

### <a name="to-attach-managed-code-extensions-to-a-document"></a>Anfügen von Erweiterungen durch verwalteten Code zu einem Dokument

1.  Fügen Sie in einem Projekt auf, die keine Microsoft Office, z. B. eine Konsolenanwendung oder eine Windows Forms-Projekt erfordert einen Verweis auf die *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* und  *Microsoft.VisualStudio.Tools.Applications.Runtime.dll* Assemblys.

2.  Fügen Sie die folgenden **Importe** oder **mit** Anweisungen am Anfang der Codedatei.

     [!code-csharp[Trin_VstcoreDeployment#4](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#4)]
     [!code-vb[Trin_VstcoreDeployment#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#4)]

3.  Rufen Sie die statische <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> Methode.

     Im folgenden Codebeispiel wird die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> überladen. Diese Überladung nimmt den vollständigen Pfad des Dokuments und einen <xref:System.Uri> , die angibt, dass des Speicherort des Bereitstellungsmanifests für die Anpassung an das Dokument angefügt werden sollen. In diesem Beispiel wird davon ausgegangen, dass ein Word-Dokument mit dem Namen **"WordDocument1.docx"** ist auf dem Desktop und das Bereitstellungsmanifest befindet sich in einem Ordner mit dem Namen **veröffentlichen** , der sich ebenfalls auf dem Desktop.

     [!code-csharp[Trin_VstcoreDeployment#3](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#3)]
     [!code-vb[Trin_VstcoreDeployment#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#3)]

4.  Erstellen Sie das Projekt, und führen Sie die Anwendung auf dem Computer, wo Sie die Anpassungen hinzufügen möchten. Der Computer muss Visual Studio 2010-Tools für Office-Laufzeit installiert sein.

## <a name="see-also"></a>Siehe auch
- [Verwalten von Dokumenten auf einem Server mit der ServerDocument-Klasse](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Vorgehensweise: Entfernen von Erweiterungen durch verwalteten Code aus Dokumenten](../vsto/how-to-remove-managed-code-extensions-from-documents.md)
- [Anwendungs- und Bereitstellungsmanifeste in Office-Projektmappen](../vsto/application-and-deployment-manifests-in-office-solutions.md)
