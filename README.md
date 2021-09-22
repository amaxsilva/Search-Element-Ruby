# Search-Element-Ruby

<h1>##########Estrutura de Mapeamento para elementos Ruby############</h1>

<h3>Para interagir com um elemento em uma página, precisamos encontrá-lo primeiro. 
O Selenium usa o que é chamado de localizador (locator) para encontrar e combinar 
os elementos na página da web.Existem 8 localizadores (locators) possíveis que o 
WebDrive nos disponibiliza:</h3>

<h2>#########Localizando por ID##########</h2>
´´´
<ul>
	#click ID
	<li>find_element(:id, "com.honda.connectedcar:id/edit_text_input").click</li> 
	#input de Dados
	<li>find_element(:id, "user_id").send_keys("texto_de_input")</li> 
	#botão
	<li>find_element(:id, "submit_btn").click</li> 
	#link
	<li>find_element(:id, "cancel_link").click</li> 
	#HTML element DIV
	<li>find_element(:id, "alert_div").click</li>
	#Validar ou comparar um texto
	<li>find_element(:id, "Usamos para validar ou comparar junto com rspec").click</li>
</ul>
´´´

<h2>#########Localizando por NAME##########</h2>
´´´
<ul>
	<li>find_element(:name, "comentario").send_keys("Este é um comentario").click</li>	
</ul>
´´´

<h2>#########Localizando por texto do link (Link Text)##########</h2>
´´´
<ul>
	#Link Text
	<li>find_element(:link_text, "Cancel").click</li>
	#link
	<li>find_element(:link, "Download").click</li>	
	#Partial Link Text - Quando queremos clicar em parte do LINK
	<li>find_element(:partial_link_text, "ncel").click</li>
</ul>
´´´ 

<h2>#########Localizando por Xpath##########</h2>
´´´
<ul>
	#Usado para mapeamento de elemento atraves de nos do XML
	<li>find_element(:xpath, "//*[@id='div2']/input[@type='checkbox']").click</li>
	´´´
	No Chrome ou nos demais navegadores, quando aciona a tecla [F12], 
	abre a Ferramente do Desenvolvedor do Navegador. Ela sim é bastante 
	útil para selecionar corretamente o XPath através de um simples passo.
	Primeiro: Localize o seu alvo através da inspeção de elemento:
	porém precisamos do XPath e para isso basta clicar com o botão direito do
	mouse sobre o element e selecionar a opção “Copy XPath”	Para ver como funciona, 
	clique [Ctrl + F] na ferramenta de desenvolvedor e cole	o resultado e veja o que acontece
	´´´
</ul>
´´´

<h2>#########Localizando por Tag Name##########</h2>

	´´´
	Existe um conjunto limitado de nomes de tags em HTML. Em outras palavras, muitos elementos compartilham a mesma tag em uma página. Normalmente não usamos o localizador ‘tag_name’ para localizar um elemento. Mas existe uma exceção:
	´´´
´´´
<ul>
	#Retorna um texto na pagina
	<li>find_element(:tag, "body").text</li>
</ul>
´´´

<h2>#########Localizando por Classe##########</h2>

´´´
<a href="back.html" class="btn btn-default">Cancel</a>
<input type="submit" class="btn btn-default btn-primary">Submit</input>
´´´
´´´
<ul>
	#Pode utilizar qualquer uma das duas formas
	<li>find_element(:class, "btn-primary").click</li>
	<li>find_element(:class, "btn).click</li>

	´´´
	O selenium não aceita nome composto
	´´´
</ul>
´´´

<h2>#########Localizando por CSS##########</h2>
´´´
<ul>
	<li>find_element(:css, "#div > input[@type='checkbox']").click</li>
</ul>
´´´

<h2>#########Utilizando uma cadeia de elementos para obter um locator##########</h2>

´´´
<div id="div1">
<input type="checkbox" name="nome" value="on">Nome do checkbox DIV 1</input>
</div>
<div id="div2">
<input type="checkbox" name="nome" value="on>Nome do checkbox DIV 2"></input>
</div>
´´´

<ul>
	#Veja que no exemplo localizei a ‘div2' pelo id e depois procurei dentro desse ‘id’ um elemento pelo nome “nome”.
	<li>find_element(:id, "div2).find_element(:name, "name").click</li>
</ul>

<h2>#########Localizando elemento em uma Combobox########</h2>

#Exemplo

´´´
<select name="birthday_month" id="month" title="Mês" class="_5dba">
	<option value="0">Mês</option>
	<option value="1">Janeiro</option>
	<option value="2">Fevereiro</option>
	<option value="3">Março</option>
	<option value="4">Abril</option>
	<option value="5">Maio</option>
	<option value="6">Junho</option>
	<option value="7">Julho</option>
	<option value="8">Agosto</option>
	<option value="9">Setembro</option>
	<option value="10">Outubro</option>
	<option value="11">Novembro</option>
	<option value="12" selected="1">Dezembro</option>
</select>
´´´

<ul>
	<li>Selenium::WeDriver::Support::Select.new(find_element(:id, "month")).select.by(:text, "Maio") find.element(:id, "month").click</li>
</ul>

<h2>#########Localizando elemento com Xpath########</h2>

#XPath no Selenium é um caminho XML usado para navegação pela estrutura HTML da página. É uma sintaxe ou linguagem para localizar qualquer #elemento em uma página da web usando a expressão de caminho XML. XPath pode ser usado para documentos HTML e XML para encontrar a #localização de qualquer elemento em uma página da web usando a estrutura HTML DOM.

´´´
Xpath = // tagname [@ attribute = 'value']
´´´
* //: Selecione o nó atual.
* Tagname: Tagname do nó particular.
* @: Selecione o atributo.
* Atributo: nome do atributo do nó.
* Valor: valor do atributo.

´´´
<div class=	"feature-box" style="height: 700px;">
	<h4>
		<b>Testando</b>
	</h4>
</div>
´´´
#Xpath Relativo
´´´
//*[@class='feature-box']//*[text()='Testando']
´´´

´´´
<input type="text" name="uid" maxlength="10" onkeyup="validateuserid();" onblur="validateuserid();">
´´´

´´´
//input[@name='uid']
´´´

#XPath básico

#Algumas expressões xpath mais básicas:
´´´
Xpath = // input [@ type = 'text']				
Xpath = // rótulo [@ id = 'message23']
Xpath = // input [@ value = 'RESET']
Xpath = // * [@ class = 'barone']
Xpath = // a [@ href = 'http: //demo.guru99.com/']
Xpath = //img[@src='//cdn.guru99.com/images/home/java.png ']	
´´´

#Contém ():
#Contains () é um método usado na expressão XPath. É usado quando o valor de qualquer atributo muda dinamicamente, por exemplo, informações #de login.

#O valor completo de 'Tipo' é 'enviar', mas usando apenas o valor parcial 'sub'.
´´´
Xpath = //*[contém(@type,'sub')]
´´´
#O valor completo de 'nome' é 'btnLogin', mas usando apenas o valor parcial 'btn'.
´´´
Xpath = //*[contém(@nome,'btn')]
´´´ 
#Usando OR & AND:
#Na expressão OR, duas condições são usadas, se a 1ª condição OU a 2ª condição devem ser verdadeiras. Também é aplicável se qualquer uma #das condições for verdadeira ou talvez ambas. Significa que qualquer condição deve ser verdadeira para encontrar o elemento.
#Na expressão XPath abaixo, ele identifica os elementos cujas condições únicas ou ambas são verdadeiras.
´´´
Xpath = // * [@ type = 'enviar' ou @ name = 'btnReset']
´´´

#Para mais informações 

#https://www.guru99.com/xpath-selenium.html
