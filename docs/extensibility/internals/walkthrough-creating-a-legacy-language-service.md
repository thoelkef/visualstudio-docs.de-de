---
title: "Exemplarische Vorgehensweise: Erstellen eines Vorgängerversion Sprachdiensts | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: language services [managed package framework], creating
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 256a609dad857097731e4914a11623fe62ad7664
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-a-legacy-language-service"></a>Exemplarische Vorgehensweise: Erstellen eines Legacy-Sprachdiensts
Verwenden der verwalteten Package Framework (MPF)-Language-Klassen zum Implementieren Sie eines Sprachdiensts in [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] ist einfach. Sie benötigen eine VSPackage zum Hosten des Sprachdiensts, der Sprachdienst selbst und einen Parser für Ihre Sprache aus.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Um dieser exemplarischen Vorgehensweise folgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../../extensibility/visual-studio-sdk.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Speicherorte für die VSPackage-Projektvorlage  
 Die Visual Studio-Paket-Projektvorlage finden Sie in die Speicherorte für drei verschiedene Vorlagen in die **neues Projekt** (Dialogfeld):  
  
1.  Unter Visual Basic-Erweiterungen. Die Standardsprache des Projekts ist Visual Basic.  
  
2.  Unter C#-Erweiterungen. Die Standardsprache des Projekts ist C#.  
  
3.  Unter den Erweiterungen für andere Projekttypen. Die Standardsprache des Projekts ist C++.  
  
### <a name="create-a-vspackage"></a>Erstellen Sie ein VSPackage  
  
1.  Erstellen Sie ein neues VSPackage, mit der Visual Studio-Paket-Projektvorlage.  
  
     Wenn Sie einen Sprachdienst für eine vorhandene VSPackage hinzufügen, überspringen Sie die folgenden Schritte aus, und fahren Sie direkt mit dem Verfahren "Erstellen der Language-Dienstklasse".  
  
2.  Geben Sie MyLanguagePackage für den Namen des Projekts, und klicken Sie auf **OK**.  
  
     Sie können einen beliebigen Namen verwenden, werden sollen. Hier detailliert vorausgesetzt MyLanguagePackage als Namen.  
  
3.  Wählen Sie [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] als die Sprache und die Option aus, um eine neue Schlüsseldatei zu generieren. Klicken Sie auf **Weiter**.  
  
4.  Geben Sie die entsprechende Unternehmen und Paket-Informationen. Klicken Sie auf **Weiter**.  
  
5.  Wählen Sie **Menübefehl**. Klicken Sie auf **Weiter**.  
  
     Wenn Sie nicht beabsichtigen, um Codeausschnitte zu unterstützen, können nur klicken Sie auf "Fertig stellen" und den nächsten Schritt ignorieren.  
  
6.  Geben Sie **Ausschnitt einfügen** als die **Befehl Name** und `cmdidInsertSnippet` für die **Befehls-ID**. Klicken Sie auf **Fertig stellen**.  
  
     Die **Befehlsname** und **Befehls-ID** kann beliebig sein, diese sind nur Beispiele.  
  
### <a name="create-the-language-service-class"></a>Erstellen Sie die Language-Dienstklasse  
  
1.  In **Projektmappen-Explorer**mit der rechten Maustaste auf das Projekt MyLanguagePackage, wählen Sie **hinzufügen**, **Verweis**, und wählen Sie dann die **neuen Verweis hinzufügen** Schaltfläche.  
  
2.  In der **Verweis hinzufügen** wählen Sie im Dialogfeld **Microsoft.VisualStudio.Package.LanguageService** in der **.NET** Registerkarte, und klicken Sie auf **OK**.  
  
     Dies muss nur einmal für die Paket-Sprachprojekt erfolgen.  
  
3.  In **Projektmappen-Explorer**mit der rechten Maustaste auf das VSPackage-Projekt, und wählen Sie **hinzufügen**, **Klasse**.  
  
4.  Stellen Sie sicher, dass **Klasse** in der Liste der Vorlagen ausgewählt ist.  
  
5.  Geben Sie **MyLanguageService.cs** für den Namen der Klassendatei und auf **hinzufügen**.  
  
     Sie können einen beliebigen Namen verwenden, werden sollen. Hier detailliert vorausgesetzt `MyLanguageService` als Namen.  
  
6.  Fügen Sie die folgenden, in der Datei MyLanguageService.cs `using` Anweisungen.  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_1.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_1.vb)]  
  
7.  Ändern der `MyLanguageService` Klasse ableiten von der <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse:  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_2.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_2.vb)]  
  
8.  Positionieren Sie den Cursor auf "LanguageService" auch von der **bearbeiten**, **IntelliSense** klicken Sie im Menü **abstrakte Klasse implementieren**. Dadurch wird die mindestens erforderlichen Methoden zum Implementieren einer Dienstklasse Sprache hinzugefügt.  
  
9. Die abstrakten Methoden implementieren, wie in beschrieben [implementieren einen Legacy-Sprachdienst](../../extensibility/internals/implementing-a-legacy-language-service2.md).  
  
### <a name="register-the-language-service"></a>Den Sprachdienst registrieren  
  
1.  Öffnen Sie die Datei MyLanguagePackagePackage.cs, und fügen Sie die folgenden `using` Anweisungen:  
  
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_3.vb)]
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_3.cs)]  
  
2.  Registrieren Sie die Language-Dienstklasse, wie in beschrieben [registrieren einen Sprachdienst Legacy](../../extensibility/internals/registering-a-legacy-language-service1.md). Dies schließt die ProvideXX Attribute und die Abschnitte "Proffering der Sprachdienst". Verwenden Sie MyLanguageService, bei denen in diesem Thema TestLanguageService verwendet.  
  
### <a name="the-parser-and-scanner"></a>Der Parser und Scanner  
  
1.  Implementieren einer Analyse und der Scanner für Ihre Sprache, wie in beschrieben [Legacy-Sprachdienstparser und Scanner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).  
  
     Wie Sie Ihre Parser und Scanner implementieren, bleibt Ihnen und ist nicht Gegenstand dieses Themas.  
  
## <a name="language-service-features"></a>Dienst-Sprachfunktionen  
 Um jede Funktion in der Sprachdienst zu implementieren, Sie in der Regel leiten Sie eine Klasse aus der entsprechenden MPF-Language-Dienstklasse, alle abstrakten Methoden implementieren, nach Bedarf und überschreiben Sie die entsprechenden Methoden. Welche Klassen erstellen und/oder abgeleitet ist abhängig von den Funktionen, die Sie unterstützen möchten. Diese Funktionen sind in im Detail besprochen [Legacy-Dienst Sprachfunktionen](../../extensibility/internals/legacy-language-service-features1.md). Das folgende Verfahren ist der allgemeine Ansatz zum Ableiten einer Klasse von die MPF-Klassen.  
  
#### <a name="deriving-from-an-mpf-class"></a>Ableiten von MPF-Klasse  
  
1.  In **Projektmappen-Explorer**mit der rechten Maustaste auf das VSPackage-Projekt, und wählen Sie **hinzufügen**, **Klasse**.  
  
2.  Stellen Sie sicher, dass **Klasse** in der Liste der Vorlagen ausgewählt ist.  
  
     Geben Sie einen geeigneten Namen für die Klassendatei, und klicken Sie auf **hinzufügen**.  
  
3.  Fügen Sie in die neue Klassendatei Folgendes `using` Anweisungen.  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_4.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_4.vb)]  
  
4.  Ändern Sie die Klasse, um die gewünschte MPF-Klasse abgeleitet.  
  
5.  Fügen Sie den Konstruktor einer Klasse, der mindestens die gleichen Parameter wie der Basisklasse-Konstruktor akzeptiert, und übergeben Sie die Konstruktorparametern an den Konstruktor der Basisklasse.  
  
     Z. B. der Konstruktor für eine Klasse ableiten, aus der <xref:Microsoft.VisualStudio.Package.Source> Klasse könnte wie folgt aussehen:  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_5.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_5.vb)]  
  
6.  Aus der **bearbeiten**, **IntelliSense** klicken Sie im Menü **abstrakte Klasse implementieren** verfügt die Basisklasse keine abstrakte Methoden, die implementiert werden müssen.  
  
7.  Andernfalls, positionieren Sie die Einfügemarke innerhalb der Klasse, und geben Sie die Methode, die außer Kraft gesetzt werden.  
  
     Geben Sie z. B. `public override` um eine Liste aller Methoden anzuzeigen, die in dieser Klasse überschrieben werden können.  
  
## <a name="see-also"></a>Siehe auch  
 [Implementieren einen Sprachdienst Legacy](../../extensibility/internals/implementing-a-legacy-language-service1.md)