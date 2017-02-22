---
title: "Exemplarische Vorgehensweise: Erstellen einer Legacy-Sprachdienst | Microsoft Docs"
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
  - "Sprachdienste [Verwaltetes Paketframework], erstellen"
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
caps.latest.revision: 19
caps.handback.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
---
# Exemplarische Vorgehensweise: Erstellen einer Legacy-Sprachdienst
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Verwenden der verwalteten Paket Framework \(MPF\) Sprache\-Klassen zum Implementieren eines Sprachdiensts in [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] ist einfach. Sie benötigen ein VSPackage zum Hosten der Sprachdienst, der Sprachdienst selbst und einen Parser für Ihre Sprache.  
  
## Vorbereitungsmaßnahmen  
 Um diese exemplarische Vorgehensweise befolgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../../extensibility/visual-studio-sdk.md).  
  
## Speicherorte für die VSPackage\-Projektvorlage  
 Die Visual Studio\-Paket\-Projektvorlage finden Sie in drei verschiedenen Stellen in der **Neues Projekt** \(Dialogfeld\):  
  
1.  Unter Visual Basic\-Erweiterbarkeit. Die Standardsprache des Projekts ist Visual Basic.  
  
2.  Unter C\#\-Erweiterbarkeit. Die Standardsprache des Projekts ist C\#.  
  
3.  Unter der Erweiterbarkeit für andere Projekttypen. Die Standardsprache des Projekts ist C\+\+.  
  
### Erstellen Sie ein VSPackage  
  
1.  Erstellen Sie ein neues VSPackage mit der Projektvorlage Visual Studio\-Paket.  
  
     Wenn Sie eine vorhandene VSPackage ein Sprachdiensts hinzufügen, überspringen Sie die folgenden Schritte und direkt mit dem Verfahren "Erstellen von the Language Service Class".  
  
2.  Geben Sie MyLanguagePackage für den Namen des Projekts, und klicken Sie auf **OK**.  
  
     Sie können einen beliebigen Namen verwenden, werden sollen. Diese Verfahren nehmen Sie MyLanguagePackage als Namen an.  
  
3.  Wählen Sie [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] als die Sprache und die Möglichkeit, eine neue Schlüsseldatei zu generieren. Klicken Sie auf **Weiter**.  
  
4.  Geben Sie die entsprechende Informationen für Unternehmen und \-Paket. Klicken Sie auf **Weiter**.  
  
5.  Wählen Sie **Menübefehl**. Klicken Sie auf **Weiter**.  
  
     Wenn Sie nicht beabsichtigen, um Codeausschnitte zu unterstützen, können Sie gerade klicken Sie auf Fertig stellen und den nächsten Schritt überspringen.  
  
6.  Geben Sie **Ausschnitt einfügen** als die **Command Name** und `cmdidInsertSnippet` für die **Befehls\-ID**. Klicken Sie auf **Fertig stellen**.  
  
     Die **Befehlsnamen** und **Befehls\-ID** kann beliebig sein, diese sind lediglich Beispiele für.  
  
### Erstellen Sie die Language\-Service\-Klasse  
  
1.  In **Projektmappen\-Explorer**, mit der rechten Maustaste auf das Projekt MyLanguagePackage, wählen Sie **Hinzufügen**, **Verweis**, und wählen Sie dann die **neuen Verweis hinzufügen** Schaltfläche.  
  
2.  In der **Verweis hinzufügen** wählen Sie im Dialogfeld **Microsoft.VisualStudio.Package.LanguageService** in der **.NET** Registerkarte, und klicken Sie auf **OK**.  
  
     Dies muss nur einmal für das Paket Sprachprojekt durchgeführt werden.  
  
3.  In **Projektmappen\-Explorer**, mit der rechten Maustaste auf das VSPackage\-Projekt, und wählen Sie **Hinzufügen**, **Klasse**.  
  
4.  Stellen Sie sicher, dass **Klasse** in der Liste der Vorlagen ausgewählt ist.  
  
5.  Geben Sie **MyLanguageService.cs** für den Namen der Klassendatei und auf **Hinzufügen**.  
  
     Sie können einen beliebigen Namen verwenden, werden sollen. Die hier angegebenen vorausgesetzt `MyLanguageService` als Namen.  
  
6.  Fügen Sie in der Datei MyLanguageService.cs die folgenden `using` Anweisungen.  
  
     [!code-cs[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_1.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_1.vb)]  
  
7.  Ändern der `MyLanguageService` Klasse ableiten der <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse:  
  
     [!code-cs[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_2.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_2.vb)]  
  
8.  Positionieren Sie den Cursor auf "LanguageService" und die **Bearbeiten**, **IntelliSense** klicken Sie im Menü **abstrakte Klasse implementieren**. Dadurch wird die mindestens erforderlichen Methoden zum Implementieren einer Sprache\-Dienstklasse hinzugefügt.  
  
9. Die abstrakten Methoden implementieren, wie in beschrieben [Implementieren eines Sprachdiensts](../../extensibility/internals/implementing-a-legacy-language-service2.md).  
  
### Registrieren des Sprachdiensts  
  
1.  Öffnen Sie die Datei MyLanguagePackagePackage.cs, und fügen Sie die folgenden `using` Anweisungen:  
  
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_3.vb)]
     [!code-cs[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_3.cs)]  
  
2.  Registrieren Ihrer Dienstklasse Sprache wie unter [Registriert eine Sprachdienst](../../extensibility/internals/registering-a-legacy-language-service1.md). Dies schließt die ProvideXX Attribute und die Abschnitte "Proffering der Sprachdienst". Verwenden Sie MyLanguageService, wobei in diesem Thema TestLanguageService verwendet.  
  
### Der Parser und Scanner  
  
1.  Implementiert einen Parser und der Scanner für Ihre Sprache wie unter [Ältere Sprachdienstparser und Scanner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).  
  
     Implementierung der Parser und Scanner ist völlig Ihnen überlassen und den Rahmen dieses Themas sprengen.  
  
## Dienst\-Sprachfunktionen  
 Um jede Funktion in der Sprachdienst zu implementieren, Sie in der Regel Ableiten einer Klasse von der entsprechenden MPF Language Service\-Klasse alle abstrakten Methoden implementieren, bei Bedarf und die entsprechenden Methoden überschreiben. Welche Klassen erstellen bzw. abgeleitet ist abhängig von den Funktionen, die Sie unterstützen möchten. Diese Funktionen werden ausführlich im [Legacy\-Dienst\-Sprachfunktionen](../../extensibility/internals/legacy-language-service-features1.md). Das folgende Verfahren ist die allgemeine Vorgehensweise zum Ableiten einer Klasse von der MPF\-Klassen.  
  
#### Ableiten von einer MPF\-Klasse  
  
1.  In **Projektmappen\-Explorer**, mit der rechten Maustaste auf das VSPackage\-Projekt, und wählen Sie **Hinzufügen**, **Klasse**.  
  
2.  Stellen Sie sicher, dass **Klasse** in der Liste der Vorlagen ausgewählt ist.  
  
     Geben Sie einen aussagekräftigen Namen für die Klassendatei, und klicken Sie auf **Hinzufügen**.  
  
3.  Fügen Sie in der neuen Klassendatei Folgendes `using` Anweisungen.  
  
     [!code-cs[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_4.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_4.vb)]  
  
4.  Ändern Sie die Klasse von der gewünschten MPF\-Klasse abgeleitet werden.  
  
5.  Fügen Sie einen Konstruktor der Klasse, der mindestens die gleichen Parameter wie der Konstruktor der Basisklasse akzeptiert, und übergeben Sie die Parameter des Konstruktors an den Konstruktor der Basisklasse.  
  
     Z. B. der Konstruktor für eine Klasse ableiten, aus der <xref:Microsoft.VisualStudio.Package.Source> Klasse könnte folgendermaßen aussehen:  
  
     [!code-cs[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_5.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_5.vb)]  
  
6.  Aus der **Bearbeiten**, **IntelliSense** klicken Sie im Menü **abstrakte Klasse implementieren** wurde die Basisklasse keine abstrakten Methoden, die implementiert werden müssen.  
  
7.  Andernfalls, positionieren Sie die Einfügemarke innerhalb der Klasse, und geben Sie die Methode außer Kraft gesetzt werden.  
  
     Geben Sie z. B. `public override` finden Sie eine Liste aller Methoden, die in dieser Klasse überschrieben werden können.  
  
## Siehe auch  
 [Implementieren einer Legacy\-Sprachdienst](../../extensibility/internals/implementing-a-legacy-language-service1.md)