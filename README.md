# projeto2_match.io
Projeto 2 Match 
import PySimpleGUI as sg 

class TelaPython:
				def __init__(self):
								# layout
								layout = [
												[sg.Text('Digite o valor do emprestimo:R$'), sg.Input(size=(10,0), key='valor')],
												[sg.Text('Digite sua renda: R$'), sg.Input(size=(10,0), key='renda')],
												[sg.Text('Quantos meses irá pagar:'), sg.Input(size=(4,0), key='meses')],
												[sg.Button('Cálcular Emprestimo' ), sg.Button('Sair') ],
												[sg.Output(size=(50,20))]
												]
								
								
								# janela
								self.janela = sg.Window('Calculo de Emprestimo').layout(layout)
								
								# extraindo dados
						
				def iniciar(self):
								while True :
												# extraindo dados
												self.button, self.values = self.janela.Read()
												
												if self.button == 'Sair':
																break
												valor = float(self.values['valor'])
												renda = float(self.values['renda'])
												meses = float(self.values['meses'])
												taxaDeJuros = meses*0.03
												prestacao = valor/meses
												prestacaoTotal = (prestacao*taxaDeJuros + prestacao)
												valorTotalEmprestimo = (prestacaoTotal * meses)

												#Validação de renda
												if prestacaoTotal > renda * 0.3: print("Infelizmente você não pode obter o empréstimo")
												else:	
													print(f'Valor da prestação mensal é: R${prestacaoTotal:,.2f}')	 
													print(f'O valor total do emprestimo ficou em: R${valorTotalEmprestimo: ,.2f}')		
														

												
tela = TelaPython()
tela.iniciar()
