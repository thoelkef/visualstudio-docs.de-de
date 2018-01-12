---
title: "Vorgehensweise: Anfügen von Erweiterungen durch verwalteten Code an Dokumente | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], attaching
- documents [Office development in Visual Studio], managed code extensions
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1653b0e903fd931d5df4b1dcce4dcbd99fbbae37
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-attach-managed-code-extensions-to-documents"></a>Gewusst wie: Anfügen von Erweiterungen durch verwalteten Code an Dokumente
  Sie können eine Anpassungsassembly an ein vorhandenes Microsoft Office Word-Dokument oder Microsoft Office Excel-Arbeitsmappe anfügen. Das Dokument oder die Arbeitsmappe kann beliebiges Dateiformat aufweisen, die von der Microsoft Office-Projekten und Entwicklungstools in Visual Studio unterstützt wird. Weitere Informationen finden Sie unter [Architektur Anpassungen auf Dokumentebene](../vsto/architecture-of-document-level-customizations.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Um eine Anpassung an ein Word- oder Excel-Dokument anzufügen, verwenden die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> Methode der <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Klasse. Da die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Klasse dient auf einem Computer ausgeführt werden, die nicht Microsoft Office installiert ist, können Sie diese Methode in Projektmappen, die nicht direkt mit Microsoft Office-Entwicklung (z. B. eine Konsolen- oder Windows Forms-Anwendung) verknüpft sind.  
  
> [!NOTE]  
>  Die Anpassung kann nicht geladen werden, wenn der Code Steuerelemente erwartet, die das angegebene Dokument nicht.  
  
 ![Link zu Video](../vsto/media/playvideo.gif "Link zu Video") eine entsprechende Videodemo finden Sie unter [wie keine I: Anfügen oder Trennen einer VSTO-Assembly aus einem Word-Dokument?](http://go.microsoft.com/fwlink/?LinkId=136782).  
  
### <a name="to-attach-managed-code-extensions-to-a-document"></a>Anfügen von Erweiterungen durch verwalteten Code zu einem Dokument  
  
1.  In einem Projekt auf, die keinen erfordert Microsoft Office, z. B. eine Konsolenanwendung oder Windows Forms-Projekt, fügen Sie einen Verweis auf die Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll und Microsoft.VisualStudio.Tools.Applications.Runtime.dll Assemblys.  
  
2.  Fügen Sie die folgenden **Importe** oder **mit** Anweisungen am Anfang der Codedatei.  
  
     [!code-csharp[Trin_VstcoreDeployment#4](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#4)]
     [!code-vb[Trin_VstcoreDeployment#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#4)]  
  
3.  Rufen Sie die statische <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> Methode.  
  
     Im folgenden Codebeispiel wird mit der <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> überladen. Diese Überladung lässt den vollständigen Pfad des Dokuments und einen <xref:System.Uri> , die angibt, dass des Speicherort des Bereitstellungsmanifests für die Anpassung des Dokuments angefügt werden soll. In diesem Beispiel wird davon ausgegangen, dass ein Word-Dokument mit dem Namen **"WordDocument1.docx"** ist auf dem Desktop und, der das Bereitstellungsmanifest befindet sich in einem Ordner mit dem Namen **veröffentlichen** , der sich ebenfalls auf dem Desktop.  
  
     [!code-csharp[Trin_VstcoreDeployment#3](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#3)]
     [!code-vb[Trin_VstcoreDeployment#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#3)]  
  
4.  Erstellen Sie das Projekt, und führen Sie die Anwendung auf dem Computer, wo Sie die Anpassung anfügen möchten. Der Computer muss Visual Studio 2010-Tools für Office-Laufzeit installiert sein.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Dokumenten auf einem Server mit der ServerDocument-Klasse](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Vorgehensweise: Entfernen von Erweiterungen durch verwalteten Code aus Dokumenten](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Anwendungs- und Bereitstellungsmanifeste in Office-Projektmappen](../vsto/application-and-deployment-manifests-in-office-solutions.md)  
  