---
title: 'Exemplarische Vorgehensweise: Erstellen eines Legacysprachdiensts | Microsoft-Dokumentation'
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
- language services [managed package framework], creating
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0d80b40aa1db779c233dea846b49dbbc66084015
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783882"
---
# <a name="walkthrough-creating-a-legacy-language-service"></a>Exemplarische Vorgehensweise: Erstellen eines Legacysprachdiensts
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Verwenden die verwaltete Package Framework (MPF) Sprache-Klassen zum Implementieren von eines Sprachdiensts im [!INCLUDE[csprcs](../../includes/csprcs-md.md)] ist einfach. Sie benötigen ein VSPackage, das den Sprachdienst, der Sprachdienst selbst und einen Parser für Ihre Sprache zu hosten.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Um diese exemplarische Vorgehensweise befolgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../../extensibility/visual-studio-sdk.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Speicherorte für die VSPackage-Projektvorlage  
 Die Visual Studio-Paket-Projektvorlage finden Sie in drei unterschiedliche Vorlagen stellen in der **neues Projekt** Dialogfeld:  
  
1.  Unter Visual Basic-Erweiterungen. Die Standardsprache des Projekts ist Visual Basic.  
  
2.  Unter C#-Erweiterungen. Die Standardsprache des Projekts ist C#.  
  
3.  Unter den Erweiterungen für andere Projekttypen. Die Standardsprache des Projekts ist C++.  
  
### <a name="create-a-vspackage"></a>Erstellen Sie ein VSPackage  
  
1.  Erstellen Sie ein neues VSPackage mit der Visual Studio-Paket-Projektvorlage aus.  
  
     Wenn Sie einen vorhandenen VSPackage einen Sprachdienst hinzufügen, überspringen Sie die folgenden Schritte und direkt mit dem Verfahren "Erstellen der Language Service Class".  
  
2.  Geben Sie MyLanguagePackage für den Namen des Projekts, und klicken Sie auf **OK**.  
  
     Sie können einen beliebigen Namen verwenden, werden sollen. Diese hier beschriebenen Verfahren davon MyLanguagePackage als den Namen aus.  
  
3.  Wählen Sie [!INCLUDE[csprcs](../../includes/csprcs-md.md)] als Sprache und die Möglichkeit, eine neue Schlüsseldatei zu generieren. Klicken Sie auf **Weiter**.  
  
4.  Geben Sie die entsprechende Informationen für Unternehmen und -Paket aus. Klicken Sie auf **Weiter**.  
  
5.  Wählen Sie **Menübefehl**. Klicken Sie auf **Weiter**.  
  
     Wenn Sie nicht beabsichtigen, um Codeausschnitte zu unterstützen, können nur klicken Sie auf "Fertig stellen" und den nächsten Schritt überspringen.  
  
6.  Geben Sie **Ausschnitt einfügen** als die **Befehlsname** und `cmdidInsertSnippet` für die **Befehls-ID**. Klicken Sie auf **Fertig stellen**.  
  
     Die **Befehlsnamen** und **Befehls-ID** kann beliebig, diese sind nur Beispiele.  
  
### <a name="create-the-language-service-class"></a>Erstellen Sie die Language-Service-Klasse  
  
1.  In **Projektmappen-Explorer**, mit der rechten Maustaste auf das MyLanguagePackage-Projekt, wählen Sie **hinzufügen**, **Verweis**, und wählen Sie dann die **neuen Verweis hinzufügen** Schaltfläche.  
  
2.  In der **Verweis hinzufügen** wählen Sie im Dialogfeld **Microsoft.VisualStudio.Package.LanguageService** in die **.NET** Registerkarte, und klicken Sie auf **OK**.  
  
     Dies muss nur einmal für die Sprache Package-Projekt durchgeführt werden.  
  
3.  In **Projektmappen-Explorer**mit der rechten Maustaste auf das VSPackage-Projekt, und wählen Sie **hinzufügen**, **Klasse**.  
  
4.  Stellen Sie sicher, dass **Klasse** in der Liste der Vorlagen ausgewählt ist.  
  
5.  Geben Sie **MyLanguageService.cs** für den Namen der Klassendatei, und klicken Sie auf **hinzufügen**.  
  
     Sie können einen beliebigen Namen verwenden, werden sollen. Diese hier beschriebenen Verfahren wird davon ausgegangen `MyLanguageService` als Namen.  
  
6.  Fügen Sie die folgenden, in der Datei MyLanguageService.cs `using` Anweisungen.  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#1](../../snippets/csharp/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/cs/mylanguageservice.cs#1)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#1](../../snippets/visualbasic/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/vb/mylanguageservice.vb#1)]  
  
7.  Ändern der `MyLanguageService` Klasse ableiten von der <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse:  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#2](../../snippets/csharp/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/cs/mylanguageservice.cs#2)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#2](../../snippets/visualbasic/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/vb/mylanguageservice.vb#2)]  
  
8.  Positionieren Sie den Cursor auf "LanguageService" und auf die **bearbeiten**, **IntelliSense** , wählen Sie im Menü **abstrakte Klasse implementieren**. Dadurch wird die mindestens erforderlichen Methoden zur Implementierung einer Sprache-Dienstklasse hinzugefügt.  
  
9. Die abstrakten Methoden implementieren, wie in beschrieben [Implementieren eines Legacysprachdiensts](../../extensibility/internals/implementing-a-legacy-language-service2.md).  
  
### <a name="register-the-language-service"></a>Registrieren des Sprachdiensts  
  
1.  Öffnen Sie die MyLanguagePackagePackage.cs-Datei, und fügen Sie die folgenden `using` Anweisungen:  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#3](../../snippets/csharp/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/cs/mylanguagepackagepackage.cs#3)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#3](../../snippets/visualbasic/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/vb/mylanguagepackagepackage.vb#3)]  
  
2.  Sprachdienstklasse registrieren, siehe [Registrieren eines Legacysprachdiensts](../../extensibility/internals/registering-a-legacy-language-service1.md). Dies schließt die ProvideXX Attribute und die "Der Sprachdienst Proffering" Abschnitte. Verwenden Sie MyLanguageService, bei denen in diesem Thema TestLanguageService verwendet.  
  
### <a name="the-parser-and-scanner"></a>Der Parser und Scanner  
  
1.  Implementiert einen Parser und Scanner für Ihre Sprache, wie in beschrieben [Legacy-Sprachdienstparser und Scanner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).  
  
     Parser und Scanner von Ihrer Implementierung der völlig Ihnen überlassen ist und über den Rahmen dieses Themas.  
  
## <a name="language-service-features"></a>Language-Service-Features  
 Um jedes Feature in den Sprachdienst zu implementieren, Sie in der Regel entsprechenden MPF sprachdienstklasse eine Klasse ableiten, implementieren jede beliebige abstrakte Methode nach Bedarf und überschreiben Sie die entsprechenden Methoden. Welche Klassen, die Sie erstellen und/oder abgeleitet ist abhängig von den Features, die Sie unterstützen möchten. Diese Funktionen werden ausführlich im [Legacy-Dienst-Sprachfeatures](../../extensibility/internals/legacy-language-service-features1.md). Das folgende Verfahren ist die allgemeine Vorgehensweise zum Ableiten einer Klasse von die MPF-Klassen.  
  
#### <a name="deriving-from-an-mpf-class"></a>Ableiten von einer MPF-Klasse  
  
1.  In **Projektmappen-Explorer**mit der rechten Maustaste auf das VSPackage-Projekt, und wählen Sie **hinzufügen**, **Klasse**.  
  
2.  Stellen Sie sicher, dass **Klasse** in der Liste der Vorlagen ausgewählt ist.  
  
     Geben Sie einen geeigneten Namen für die Klassendatei, und klicken Sie auf **hinzufügen**.  
  
3.  Fügen Sie in der neuen Klassendatei Folgendes `using` Anweisungen.  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#4](../../snippets/csharp/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/cs/mysource.cs#4)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#4](../../snippets/visualbasic/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/vb/mysource.vb#4)]  
  
4.  Ändern Sie die Klasse auf die gewünschte MPF-Klasse abgeleitet.  
  
5.  Fügen Sie den Konstruktor einer Klasse, der mindestens die gleichen Parameter wie der Konstruktor der Basisklasse akzeptiert, und übergeben Sie die Parameter des Konstruktors an den Basisklassenkonstruktor zu.  
  
     Z. B. der Konstruktor für eine Klasse abgeleitet der <xref:Microsoft.VisualStudio.Package.Source> Klasse könnte wie folgt aussehen:  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#5](../../snippets/csharp/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/cs/mysource.cs#5)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#5](../../snippets/visualbasic/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/vb/mysource.vb#5)]  
  
6.  Von der **bearbeiten**, **IntelliSense** , wählen Sie im Menü **abstrakte Klasse implementieren** verfügt die Basisklasse keine abstrakten Methoden, die implementiert werden müssen.  
  
7.  Andernfalls positionieren Sie die Einfügemarke innerhalb der Klasse zu, und geben Sie die Methode außer Kraft gesetzt werden.  
  
     Geben Sie z. B. `public override` um eine Liste aller Methoden, die in dieser Klasse überschrieben werden können.  
  
## <a name="see-also"></a>Siehe auch  
 [Implementieren eines Legacysprachdiensts](../../extensibility/internals/implementing-a-legacy-language-service1.md)

