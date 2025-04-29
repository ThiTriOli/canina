import UIKit

class ViewController: UIViewController {
    
    @IBOutlet weak var ageTextField: UITextField!
    @IBOutlet weak var resultLabel: UILabel!
    
    override func viewDidLoad() {
        super.viewDidLoad()
    }
    
    @IBAction func calculateButtonPressed(_ sender: UIButton) {
        if let humanAge = Int(ageTextField.text ?? "0") {
            let dogAge = calculateDogAge(humanAge: humanAge)
            resultLabel.text = "Idade canina: \(dogAge) anos"
        } else {
            resultLabel.text = "Digite uma idade válida"
        }
        ageTextField.resignFirstResponder()
    }
    
    func calculateDogAge(humanAge: Int) -> Double {
        return humanAge <= 2 ? Double(humanAge) * 10.5 : 21 + Double(humanAge - 2) * 4
    }
}
Como implementar:
Crie um novo projeto no Xcode

No Main.storyboard:

Adicione um TextField (para entrada da idade humana)

Adicione um Button (para acionar o cálculo)

Adicione um Label (para mostrar o resultado)

Conecte os outlets e actions no código (Ctrl+Arrastar)

Conecte o TextField para ageTextField

Conecte o Label para resultLabel

Conecte a ação do botão para calculateButtonPressed

import SwiftUI



struct ContentView: View {

    @State private var username: String = ""

    @State private var password: String = ""

    @State private var isPasswordVisible: Bool = false



    var body: some View {

        VStack {

            Spacer()



            VStack(spacing: 20) {

                TextField("Digite o nome de usuário", text: $username)

                    .padding()

                    .cornerRadius(10)

                    .frame(width: 250)



                ZStack(alignment: .trailing) {

                    Group {

                        if isPasswordVisible {

                            TextField("Digite sua senha", text: $password)

                        } else {

                            SecureField("Digite sua senha", text: $password)

                        }

                    }

                    .keyboardType(.numberPad)

                    .padding()

                    .cornerRadius(10)

                    .frame(width: 250)



                    Button(action: {

                        isPasswordVisible.toggle()

                    }) {

                        Image(systemName: isPasswordVisible ? "eye.slash.fill" : "eye.fill")

                            .foregroundColor(.black)

                            .padding(.trailing, 15)

                    }

                }

            }

            .padding(.bottom, 40)

        }

        .frame(maxHeight: .infinity, alignment: .bottom)

        .ignoresSafeArea(.keyboard, edges: .bottom)

    }

}



struct ContentView_Previews: PreviewProvider {

    static var previews: some View {

        ContentView()

    }

}
