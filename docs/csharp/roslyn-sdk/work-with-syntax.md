---
title: Usar el modelo de sintaxis del SDK de .NET Compiler Platform
description: "En este tema se proporciona una descripción de los tipos que se usan para entender y manipular nodos de sintaxis."
author: billwagner
ms.author: wiwagn
ms.date: 10/15/2017
ms.topic: conceptual
ms.prod: .net
ms.devlang: devlang-csharp
ms.custom: mvc
ms.openlocfilehash: 09d07e6257ad7d32d75328a8c1850888b4d0b937
ms.sourcegitcommit: 099aa20d9b6450d1b7452d782a55771a6ad8ff35
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/05/2018
---
# <a name="work-with-syntax"></a><span data-ttu-id="0b4eb-103">Trabajar con sintaxis</span><span class="sxs-lookup"><span data-stu-id="0b4eb-103">Work with syntax</span></span>

<span data-ttu-id="0b4eb-104">El **árbol de sintaxis** es una estructura de datos fundamental expuesta por las API del compilador.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-104">The **syntax tree** is a fundamental data structure exposed by the compiler APIs.</span></span> <span data-ttu-id="0b4eb-105">Estos árboles representan la estructura léxica y sintáctica del código fuente.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-105">These trees represent the lexical and syntactic structure of source code.</span></span> <span data-ttu-id="0b4eb-106">Tienen dos importantes finalidades:</span><span class="sxs-lookup"><span data-stu-id="0b4eb-106">They serve two important purposes:</span></span>

1. <span data-ttu-id="0b4eb-107">Permitir herramientas, como un IDE, complementos, herramientas de análisis de código y refactorizaciones, para ver y procesar la estructura sintáctica del código fuente del proyecto de un usuario.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-107">To allow tools - such as an IDE, add-ins, code analysis tools, and refactorings - to see and process the syntactic structure of source code in a user’s project.</span></span>
2. <span data-ttu-id="0b4eb-108">Habilitar herramientas, como refactorizaciones y un IDE, para crear, modificar y reorganizar el código fuente de forma natural sin tener que usar ediciones de texto directas.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-108">To enable tools - such as refactorings and an IDE - to create, modify, and rearrange source code in a natural manner without having use direct text edits.</span></span> <span data-ttu-id="0b4eb-109">Al crear y manipular árboles, las herramientas pueden crear y reorganizar fácilmente el código fuente.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-109">By creating and manipulating trees, tools can easily create and rearrange source code.</span></span>

## <a name="syntax-trees"></a><span data-ttu-id="0b4eb-110">Árboles de sintaxis</span><span class="sxs-lookup"><span data-stu-id="0b4eb-110">Syntax trees</span></span>

<span data-ttu-id="0b4eb-111">Los árboles de sintaxis son la estructura principal usada para la compilación, el análisis de código, los enlaces, la refactorización, las características de IDE y la generación de código.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-111">Syntax trees are the primary structure used for compilation, code analysis, binding, refactoring, IDE features, and code generation.</span></span> <span data-ttu-id="0b4eb-112">Ninguna parte del código fuente se entiende sin que primero se haya identificado y clasificado en alguno de los elementos de lenguaje estructural conocidos.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-112">No part of the source code is understood without it first being identified and categorized into one of many well-known structural language elements.</span></span> 

<span data-ttu-id="0b4eb-113">Los árboles de sintaxis tienen tres atributos clave.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-113">Syntax trees have three key attributes.</span></span> <span data-ttu-id="0b4eb-114">El primer atributo es que los árboles de sintaxis contienen toda la información de origen con plena fidelidad.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-114">The first attribute is that syntax trees hold all the source information in full fidelity.</span></span> <span data-ttu-id="0b4eb-115">Esto significa que el árbol de sintaxis contiene cada fragmento de información del texto de origen, cada construcción gramatical, cada token léxico y todo lo que hay entre estos elementos, incluidos los espacios en blanco, los comentarios y las directivas de preprocesador.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-115">This means that the syntax tree contains every piece of information found in the source text, every grammatical construct, every lexical token, and everything else in between, including whitespace, comments, and preprocessor directives.</span></span> <span data-ttu-id="0b4eb-116">Por ejemplo, cada literal mencionado en el origen se representa exactamente como se ha escrito.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-116">For example, each literal mentioned in the source is represented exactly as it was typed.</span></span> <span data-ttu-id="0b4eb-117">Los árboles de sintaxis también representan errores del código fuente cuando el programa está incompleto o tiene un formato incorrecto mediante la representación de tokens omitidos o que faltan en el árbol de sintaxis.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-117">The syntax trees also represent errors in source code when the program is incomplete or malformed by representing skipped or missing tokens in the syntax tree.</span></span>  

<span data-ttu-id="0b4eb-118">Esto habilita el segundo atributo de los árboles de sintaxis.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-118">This enables the second attribute of syntax trees.</span></span> <span data-ttu-id="0b4eb-119">Un árbol de sintaxis obtenido del analizador puede generar el texto exacto a partir del que se ha analizado.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-119">A syntax tree obtained from the parser can produce the exact text it was parsed from.</span></span> <span data-ttu-id="0b4eb-120">Es posible obtener la representación de texto del subárbol cuya raíz está en ese nodo desde cualquier nodo de sintaxis.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-120">From any syntax node, it is possible to get the text representation of the sub-tree rooted at that node.</span></span> <span data-ttu-id="0b4eb-121">Esto significa que los árboles de sintaxis se pueden usar como una manera de crear y editar texto de origen.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-121">This means that syntax trees can be used as a way to construct and edit source text.</span></span> <span data-ttu-id="0b4eb-122">Al crear un árbol, implícitamente se ha creado el texto equivalente, mientras que al editar un árbol de sintaxis o crear uno nuevo a partir de los cambios en uno existente, se ha editado realmente el texto.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-122">By creating a tree you have by implication created the equivalent text, and by editing a syntax tree, making a new tree out of changes to an existing tree, you have effectively edited the text.</span></span> 

<span data-ttu-id="0b4eb-123">El tercer atributo de los árboles de sintaxis es que son inmutables y seguros para subprocesos.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-123">The third attribute of syntax trees is that they are immutable and thread-safe.</span></span>  <span data-ttu-id="0b4eb-124">Esto significa que una vez obtenido un árbol, es una instantánea del estado actual del código y nunca cambia.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-124">This means that after a tree is obtained, it is a snapshot of the current state of the code, and never changes.</span></span> <span data-ttu-id="0b4eb-125">Esto permite que varios usuarios interactúen con el mismo árbol de sintaxis a la vez en distintos subprocesos sin que se produzca ningún bloqueo ni duplicación.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-125">This allows multiple users to interact with the same syntax tree at the same time in different threads without locking or duplication.</span></span> <span data-ttu-id="0b4eb-126">Dado que los árboles son inmutables y no permiten ninguna modificación directa, los métodos de fábrica ayudan a crear y modificar los árboles de sintaxis mediante la creación de instantáneas adicionales del árbol.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-126">Because the trees are immutable and no modifications can be made directly to a tree, factory methods help create and modify syntax trees by creating additional snapshots of the tree.</span></span> <span data-ttu-id="0b4eb-127">Los árboles son eficaces en su forma de volver a usar nodos subyacentes, así que es posible volver a crear una nueva versión rápidamente y con poca memoria adicional.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-127">The trees are efficient in the way they reuse underlying nodes, so a new version can be rebuilt fast and with little extra memory.</span></span>

<span data-ttu-id="0b4eb-128">Un árbol de sintaxis es literalmente una estructura de datos de árbol donde los elementos estructurales no terminales son primarios con respecto a otros elementos.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-128">A syntax tree is literally a tree data structure, where non-terminal structural elements parent other elements.</span></span> <span data-ttu-id="0b4eb-129">Cada árbol de sintaxis se compone de nodos, tokens y curiosidades.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-129">Each syntax tree is made up of nodes, tokens, and trivia.</span></span>  

## <a name="syntax-nodes"></a><span data-ttu-id="0b4eb-130">Nodos de sintaxis</span><span class="sxs-lookup"><span data-stu-id="0b4eb-130">Syntax nodes</span></span>

<span data-ttu-id="0b4eb-131">Los nodos de sintaxis son uno de los elementos principales de los árboles de sintaxis.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-131">Syntax nodes are one of the primary elements of syntax trees.</span></span> <span data-ttu-id="0b4eb-132">Estos nodos representan construcciones sintácticas como declaraciones, instrucciones, cláusulas y expresiones.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-132">These nodes represent syntactic constructs such as declarations, statements, clauses, and expressions.</span></span> <span data-ttu-id="0b4eb-133">Cada categoría de nodos de sintaxis se representa mediante una clase independiente derivada de <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-133">Each category of syntax nodes is represented by a separate class derived from <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0b4eb-134">El conjunto de clases de nodos no es extensible.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-134">The set of node classes is not extensible.</span></span> 

<span data-ttu-id="0b4eb-135">Todos los nodos de sintaxis son nodos no terminales del árbol de sintaxis, lo que significa que siempre tienen otros nodos y tokens como elementos secundarios.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-135">All syntax nodes are non-terminal nodes in the syntax tree, which means they always have other nodes and tokens as children.</span></span> <span data-ttu-id="0b4eb-136">Como elemento secundario de otro nodo, cada nodo tiene un nodo principal al que se puede acceder mediante la propiedad <xref:Microsoft.CodeAnalysis.SyntaxNode.Parent?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-136">As a child of another node, each node has a parent node that can be accessed through the <xref:Microsoft.CodeAnalysis.SyntaxNode.Parent?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="0b4eb-137">Dado que los nodos y los árboles son inmutables, el elemento principal de un nodo nunca cambia.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-137">Because nodes and trees are immutable, the parent of a node never changes.</span></span> <span data-ttu-id="0b4eb-138">La raíz del árbol tiene un elemento principal nulo.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-138">The root of the tree has a null parent.</span></span>  

<span data-ttu-id="0b4eb-139">Cada nodo tiene un método <xref:Microsoft.CodeAnalysis.SyntaxNode.ChildNodes?displayProperty=nameWithType> que devuelve una lista de nodos secundarios en orden secuencial según su posición en el texto de origen.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-139">Each node has a <xref:Microsoft.CodeAnalysis.SyntaxNode.ChildNodes?displayProperty=nameWithType> method, which returns a list of child nodes in sequential order based on their position in the source text.</span></span> <span data-ttu-id="0b4eb-140">Esta lista no contiene tokens.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-140">This list does not contain tokens.</span></span> <span data-ttu-id="0b4eb-141">Cada nodo también tiene métodos para examinar descendientes, como <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A>, <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantTokens%2A> o <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantTrivia%2A>, que representan una lista de todos los nodos, tokens o curiosidades que existen en el subárbol cuya raíz está en ese nodo.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-141">Each node also has methods to examine Descendants, such as <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A>, <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantTokens%2A>, or <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantTrivia%2A> - that represent a list of all the nodes, tokens, or trivia, that exist in the sub-tree rooted by that node.</span></span>  

<span data-ttu-id="0b4eb-142">Además, cada subclase de nodos de sintaxis expone los mismos elementos secundarios mediante propiedades fuertemente tipadas.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-142">In addition, each syntax node subclass exposes all the same children through strongly typed properties.</span></span> <span data-ttu-id="0b4eb-143">Por ejemplo, una clase de nodos <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax> tiene tres propiedades adicionales específicas de los operadores binarios: <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left>, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken> y <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right>.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-143">For example, a <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax> node class has three additional properties specific to binary operators: <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left>, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken>, and <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right>.</span></span> <span data-ttu-id="0b4eb-144">El tipo de <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left> y <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right> es <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ExpressionSyntax>, y el tipo de <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken> es <xref:Microsoft.CodeAnalysis.SyntaxToken>.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-144">The type of <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left> and <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right> is <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ExpressionSyntax>, and the type of <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken> is <xref:Microsoft.CodeAnalysis.SyntaxToken>.</span></span>

<span data-ttu-id="0b4eb-145">Algunos nodos de sintaxis tienen elementos secundarios opcionales.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-145">Some syntax nodes have optional children.</span></span> <span data-ttu-id="0b4eb-146">Por ejemplo, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IfStatementSyntax> tiene un elemento opcional <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ElseClauseSyntax>.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-146">For example, an <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IfStatementSyntax> has an optional <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ElseClauseSyntax>.</span></span> <span data-ttu-id="0b4eb-147">Si el elemento secundario no está presente, la propiedad devuelve null.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-147">If the child is not present, the property returns null.</span></span> 

## <a name="syntax-tokens"></a><span data-ttu-id="0b4eb-148">Tokens de sintaxis</span><span class="sxs-lookup"><span data-stu-id="0b4eb-148">Syntax tokens</span></span>

<span data-ttu-id="0b4eb-149">Los tokens de sintaxis son los terminales de la gramática del lenguaje y representan los fragmentos sintácticos más pequeños del código.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-149">Syntax tokens are the terminals of the language grammar, representing the smallest syntactic fragments of the code.</span></span> <span data-ttu-id="0b4eb-150">Nunca son elementos principales de otros nodos o tokens.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-150">They are never parents of other nodes or tokens.</span></span> <span data-ttu-id="0b4eb-151">Los tokens de sintaxis constan de palabras clave, identificadores, literales y signos de puntuación.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-151">Syntax tokens consist of keywords, identifiers, literals, and punctuation.</span></span> 

<span data-ttu-id="0b4eb-152">Por eficacia, el tipo <xref:Microsoft.CodeAnalysis.SyntaxToken> es un tipo de valor CLR.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-152">For efficiency purposes, the <xref:Microsoft.CodeAnalysis.SyntaxToken> type is a CLR value type.</span></span> <span data-ttu-id="0b4eb-153">Por tanto, a diferencia de los nodos de sintaxis, solo hay una estructura para todos los tipos de tokens con una mezcla de propiedades que tienen significado según el tipo de token que se va a representar.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-153">Therefore, unlike syntax nodes, there is only one structure for all kinds of tokens with a mix of properties that have meaning depending on the kind of token that is being represented.</span></span>

<span data-ttu-id="0b4eb-154">Por ejemplo, un token de literal entero representa un valor numérico.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-154">For example, an integer literal token represents a numeric value.</span></span> <span data-ttu-id="0b4eb-155">Además del texto de origen sin formato que abarca el token, el token de literal tiene una propiedad <xref:Microsoft.CodeAnalysis.SyntaxToken.Value> que indica el valor entero descodificado exacto.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-155">In addition to the raw source text the token spans, the literal token has a <xref:Microsoft.CodeAnalysis.SyntaxToken.Value> property that tells you the exact decoded integer value.</span></span> <span data-ttu-id="0b4eb-156">El tipo de esta propiedad se considera <xref:System.Object>, ya que puede ser alguno de los tipos primitivos.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-156">This property is typed as <xref:System.Object> because it may be one of many primitive types.</span></span>

<span data-ttu-id="0b4eb-157">La propiedad <xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> transmite la misma información que la propiedad <xref:Microsoft.CodeAnalysis.SyntaxToken.Value>; pero el tipo de esta propiedad siempre es <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-157">The <xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> property tells you the same information as the <xref:Microsoft.CodeAnalysis.SyntaxToken.Value> property; however this property is always typed as <xref:System.String>.</span></span> <span data-ttu-id="0b4eb-158">Un identificador en el texto de origen C# puede incluir caracteres de escape Unicode, aunque la sintaxis de la propia secuencia de escape no se considera parte del nombre del identificador.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-158">An identifier in C# source text may include Unicode escape characters, yet the syntax of the escape sequence itself is not considered part of the identifier name.</span></span> <span data-ttu-id="0b4eb-159">Por tanto, aunque el texto sin formato que abarca el token incluye la secuencia de escape, la propiedad <xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> no.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-159">So although the raw text spanned by the token does include the escape sequence, the <xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> property does not.</span></span> <span data-ttu-id="0b4eb-160">En su lugar, incluye los caracteres Unicode que identifica el escape.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-160">Instead, it includes the Unicode characters identified by the escape.</span></span> <span data-ttu-id="0b4eb-161">Por ejemplo, si el texto de origen contiene un identificador escrito como `\u03C0`, la propiedad <xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> de este token devuelve `π`.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-161">For example, if the source text contains an identifier written as `\u03C0`, then the <xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> property for this token will return `π`.</span></span>

## <a name="syntax-trivia"></a><span data-ttu-id="0b4eb-162">Curiosidades de sintaxis</span><span class="sxs-lookup"><span data-stu-id="0b4eb-162">Syntax trivia</span></span>

<span data-ttu-id="0b4eb-163">Las curiosidades de sintaxis representan las partes del texto de origen que no son significativas para el normal entendimiento del código, como los espacios en blanco, los comentarios y las directivas de preprocesador.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-163">Syntax trivia represent the parts of the source text that are largely insignificant for normal understanding of the code, such as whitespace, comments, and preprocessor directives.</span></span> <span data-ttu-id="0b4eb-164">Al igual que los tokens de sintaxis, las curiosidades son tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-164">Like syntax tokens, trivia are value types.</span></span> <span data-ttu-id="0b4eb-165">Se usa el tipo único <xref:Microsoft.CodeAnalysis.SyntaxTrivia?displayProperty=nameWithType> para describir todos los tipos de curiosidades.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-165">The single <xref:Microsoft.CodeAnalysis.SyntaxTrivia?displayProperty=nameWithType> type is used to describe all kinds of trivia.</span></span>

<span data-ttu-id="0b4eb-166">Dado que las curiosidades no forman parte de la sintaxis normal del lenguaje y pueden aparecer en cualquier lugar entre dos tokens, no se incluyen en el árbol de sintaxis como elemento secundario de un nodo.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-166">Because trivia are not part of the normal language syntax and can appear anywhere between any two tokens, they are not included in the syntax tree as a child of a node.</span></span> <span data-ttu-id="0b4eb-167">Pero dado que son importantes a la hora de implementar una característica como la refactorización y de mantener la plena fidelidad con el texto de origen, existen como parte del árbol de sintaxis.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-167">Yet, because they are important when implementing a feature like refactoring and to maintain full fidelity with the source text, they do exist as part of the syntax tree.</span></span>

<span data-ttu-id="0b4eb-168">Puede acceder a las curiosidades si inspecciona las colecciones <xref:Microsoft.CodeAnalysis.SyntaxToken.LeadingTrivia?displayProperty=nameWithType> o <xref:Microsoft.CodeAnalysis.SyntaxToken.TrailingTrivia?displayProperty=nameWithType> de un token.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-168">You can access trivia by inspecting a token’s <xref:Microsoft.CodeAnalysis.SyntaxToken.LeadingTrivia?displayProperty=nameWithType> or <xref:Microsoft.CodeAnalysis.SyntaxToken.TrailingTrivia?displayProperty=nameWithType> collections.</span></span> <span data-ttu-id="0b4eb-169">Cuando se analiza el texto de origen, las secuencias de curiosidades se asocian a los tokens.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-169">When source text is parsed, sequences of trivia are associated with tokens.</span></span> <span data-ttu-id="0b4eb-170">En general, un token es propietario de cualquier curiosidad que le preceda en la misma línea hasta el siguiente token.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-170">In general, a token owns any trivia after it on the same line up to the next token.</span></span> <span data-ttu-id="0b4eb-171">Cualquier curiosidad situada después de esa línea se asocia al token siguiente.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-171">Any trivia after that line is associated with the following token.</span></span> <span data-ttu-id="0b4eb-172">El primer token del archivo de origen obtiene todas las curiosidades iniciales, mientras que la última secuencia de curiosidades del archivo se agrega al último token del archivo, que, de lo contrario, tiene ancho de cero.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-172">The first token in the source file gets all the initial trivia, and the last sequence of trivia in the file is tacked onto the end-of-file token, which otherwise has zero width.</span></span>

<span data-ttu-id="0b4eb-173">A diferencia de los nodos y los tokens de sintaxis, las curiosidades de sintaxis no tienen elementos principales.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-173">Unlike syntax nodes and tokens, syntax trivia do not have parents.</span></span> <span data-ttu-id="0b4eb-174">Pero, dado que forman parte del árbol y cada una está asociada a un token único, se puede acceder al token con el que está asociada mediante la propiedad <xref:Microsoft.CodeAnalysis.SyntaxTrivia.Token?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-174">Yet, because they are part of the tree and each is associated with a single token, you may access the token it is associated with using the <xref:Microsoft.CodeAnalysis.SyntaxTrivia.Token?displayProperty=nameWithType> property.</span></span>

## <a name="spans"></a><span data-ttu-id="0b4eb-175">Intervalos</span><span class="sxs-lookup"><span data-stu-id="0b4eb-175">Spans</span></span>

<span data-ttu-id="0b4eb-176">Cada nodo, token o curiosidad conoce su posición dentro del texto de origen y el número de caracteres del que se compone.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-176">Each node, token, or trivia knows its position within the source text and the number of characters it consists of.</span></span> <span data-ttu-id="0b4eb-177">Una posición de texto se representa como un entero de 32 bits, que es un índice `char` de base cero.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-177">A text position is represented as a 32-bit integer, which is a zero-based `char` index.</span></span> <span data-ttu-id="0b4eb-178">Un objeto <xref:Microsoft.CodeAnalysis.Text.TextSpan> es la posición inicial y un recuento de caracteres, ambos representados como enteros.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-178">A <xref:Microsoft.CodeAnalysis.Text.TextSpan> object is the beginning position and a count of characters, both represented as integers.</span></span> <span data-ttu-id="0b4eb-179">Si <xref:Microsoft.CodeAnalysis.Text.TextSpan> tiene una longitud cero, hace referencia a una ubicación entre dos caracteres.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-179">If <xref:Microsoft.CodeAnalysis.Text.TextSpan> has a zero length, it refers to a location between two characters.</span></span>

<span data-ttu-id="0b4eb-180">Cada nodo tiene dos propiedades <xref:Microsoft.CodeAnalysis.Text.TextSpan>: <xref:Microsoft.CodeAnalysis.SyntaxNode.Span*> y <xref:Microsoft.CodeAnalysis.SyntaxNode.FullSpan*>.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-180">Each node has two <xref:Microsoft.CodeAnalysis.Text.TextSpan> properties: <xref:Microsoft.CodeAnalysis.SyntaxNode.Span*> and <xref:Microsoft.CodeAnalysis.SyntaxNode.FullSpan*>.</span></span> 

<span data-ttu-id="0b4eb-181">La propiedad <xref:Microsoft.CodeAnalysis.SyntaxNode.Span\*> es el intervalo de texto desde el principio del primer token del subárbol del nodo al final del último token.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-181">The <xref:Microsoft.CodeAnalysis.SyntaxNode.Span\*> property is the text span from the start of the first token in the node’s sub-tree to the end of the last token.</span></span> <span data-ttu-id="0b4eb-182">Este intervalo no incluye ninguna curiosidad inicial ni final.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-182">This span does not include any leading or trailing trivia.</span></span>

<span data-ttu-id="0b4eb-183">La propiedad <xref:Microsoft.CodeAnalysis.SyntaxNode.FullSpan\*> es el intervalo de texto que incluye el intervalo normal del nodo, así como el intervalo de cualquier curiosidad inicial o final.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-183">The <xref:Microsoft.CodeAnalysis.SyntaxNode.FullSpan\*> property is the text span that includes the node’s normal span, plus the span of any leading or trailing trivia.</span></span>

<span data-ttu-id="0b4eb-184">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="0b4eb-184">For example:</span></span> 

``` csharp
      if (x > 3)
      {
||        // this is bad
          |throw new Exception("Not right.");|  // better exception?||
      }
```

<span data-ttu-id="0b4eb-185">El nodo de la instrucción dentro del bloque tiene un intervalo indicado por las plecas (|).</span><span class="sxs-lookup"><span data-stu-id="0b4eb-185">The statement node inside the block has a span indicated by the single vertical bars (|).</span></span> <span data-ttu-id="0b4eb-186">Incluye los caracteres `throw new Exception("Not right.");`.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-186">It includes the characters `throw new Exception("Not right.");`.</span></span> <span data-ttu-id="0b4eb-187">Las plecas dobles (||) indican el intervalo completo.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-187">The full span is indicated by the double vertical bars (||).</span></span> <span data-ttu-id="0b4eb-188">Incluye los mismos caracteres que el intervalo y los caracteres asociados a las curiosidades inicial y final.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-188">It includes the same characters as the span and the characters associated with the leading and trailing trivia.</span></span>

## <a name="kinds"></a><span data-ttu-id="0b4eb-189">Tipos</span><span class="sxs-lookup"><span data-stu-id="0b4eb-189">Kinds</span></span>

<span data-ttu-id="0b4eb-190">Cada nodo, token o curiosidad tiene una propiedad <xref:Microsoft.CodeAnalysis.SyntaxNode.RawKind?displayProperty=nameWithType>, de tipo <xref:System.Int32?displayProperty=nameWithType>, que identifica el elemento de sintaxis exacto representado.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-190">Each node, token, or trivia has a <xref:Microsoft.CodeAnalysis.SyntaxNode.RawKind?displayProperty=nameWithType> property, of type <xref:System.Int32?displayProperty=nameWithType>, that identifies the exact syntax element represented.</span></span> <span data-ttu-id="0b4eb-191">Este valor se puede convertir en una enumeración específica del lenguaje; cada lenguaje, C# o VB, tiene una sola enumeración `SyntaxKind` (<xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind?displayProperty=nameWithType> y <xref:Microsoft.CodeAnalysis.VisualBasic.SyntaxKind?displayProperty=nameWithType>, respectivamente) que enumera todos los posibles nodos, tokens y curiosidades de la gramática.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-191">This value can be cast to a language-specific enumeration; each language, C# or VB, has a single `SyntaxKind` enumeration  (<xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind?displayProperty=nameWithType> and <xref:Microsoft.CodeAnalysis.VisualBasic.SyntaxKind?displayProperty=nameWithType>, respectively) that lists all the possible nodes, tokens, and trivia elements in the grammar.</span></span> <span data-ttu-id="0b4eb-192">Esta conversión se puede realizar automáticamente al acceder a los métodos de extensión <xref:Microsoft.CodeAnalysis.CSharp.CSharpExtensions.Kind*?displayProperty=nameWithType> o <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicExtensions.Kind*?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-192">This conversion can be done automatically by accessing the <xref:Microsoft.CodeAnalysis.CSharp.CSharpExtensions.Kind*?displayProperty=nameWithType> or <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicExtensions.Kind*?displayProperty=nameWithType> extension methods.</span></span>

<span data-ttu-id="0b4eb-193">La propiedad <xref:Microsoft.CodeAnalysis.SyntaxToken.RawKind> permite anular fácilmente la ambigüedad de los tipos de nodos de sintaxis que comparten la misma clase de nodos.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-193">The <xref:Microsoft.CodeAnalysis.SyntaxToken.RawKind> property allows for easy disambiguation of syntax node types that share the same node class.</span></span> <span data-ttu-id="0b4eb-194">En el caso de los tokens y las curiosidades, esta propiedad es la única manera de distinguir un tipo de elemento de otro.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-194">For tokens and trivia, this property is the only way to distinguish one type of element from another.</span></span> 

<span data-ttu-id="0b4eb-195">Por ejemplo, una sola clase <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax> tiene <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left>, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken> y <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right> como elementos secundarios.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-195">For example, a single <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax> class has <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left>, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken>, and <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right> as children.</span></span> <span data-ttu-id="0b4eb-196">La propiedad <xref:Microsoft.CodeAnalysis.CSharp.CSharpExtensions.Kind\*> distingue si es un tipo <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.AddExpression>, <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.SubtractExpression> o <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.MultiplyExpression> de nodo de sintaxis.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-196">The <xref:Microsoft.CodeAnalysis.CSharp.CSharpExtensions.Kind\*> property distinguishes whether it is an <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.AddExpression>, <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.SubtractExpression>, or <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.MultiplyExpression> kind of syntax node.</span></span>

## <a name="errors"></a><span data-ttu-id="0b4eb-197">Errores</span><span class="sxs-lookup"><span data-stu-id="0b4eb-197">Errors</span></span>

<span data-ttu-id="0b4eb-198">Aunque el texto de origen contenga errores de sintaxis, se expone un árbol de sintaxis completo con recorrido de ida y vuelta al origen.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-198">Even when the source text contains syntax errors, a full syntax tree that is round-trippable to the source is exposed.</span></span> <span data-ttu-id="0b4eb-199">Si el analizador detecta código que no se ajusta a la sintaxis definida del lenguaje, usa una de estas dos técnicas para crear un árbol de sintaxis.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-199">When the parser encounters code that does not conform to the defined syntax of the language, it uses one of two techniques to create a syntax tree.</span></span>

<span data-ttu-id="0b4eb-200">En primer lugar, si el analizador espera un determinado tipo de token pero no lo encuentra, puede insertar un token que falta en el árbol de sintaxis en la ubicación esperada del token.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-200">First, if the parser expects a particular kind of token but does not find it, it may insert a missing token into the syntax tree in the location that the token was expected.</span></span> <span data-ttu-id="0b4eb-201">Un token que falta representa el token real esperado, aunque tiene un intervalo vacío y su propiedad <xref:Microsoft.CodeAnalysis.SyntaxNode.IsMissing?displayProperty=nameWithType> devuelve `true`.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-201">A missing token represents the actual token that was expected, but it has an empty span, and its <xref:Microsoft.CodeAnalysis.SyntaxNode.IsMissing?displayProperty=nameWithType> property returns `true`.</span></span>

<span data-ttu-id="0b4eb-202">En segundo lugar, el analizador puede omitir tokens hasta encontrar uno en el que pueda seguir analizando.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-202">Second, the parser may skip tokens until it finds one where it can continue parsing.</span></span> <span data-ttu-id="0b4eb-203">En este caso, los tokens omitidos se adjuntan como un nodo de curiosidades con el tipo <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.SkippedTokensTrivia>.</span><span class="sxs-lookup"><span data-stu-id="0b4eb-203">In this case, the skipped tokens are attached as a trivia node with the kind <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.SkippedTokensTrivia>.</span></span>