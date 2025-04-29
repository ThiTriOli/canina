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
