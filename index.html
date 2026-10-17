import SwiftUI
import Combine

struct Exercise: Identifiable {
    let id = UUID()
    let name: String
    let duration: Int
    let instruction: String
    let intensityMET: Double
    let symbol: String
}

@MainActor
final class WorkoutModel: ObservableObject {
    @Published var weightKg: Double = 90
    @Published var currentIndex = 0
    @Published var secondsLeft = 240
    @Published var isRunning = false
    @Published var elapsedSeconds = 0
    @Published var completed = false

    let exercises: [Exercise] = [
        .init(name: "Aquecimento leve", duration: 4 * 60,
              instruction: "Marche sem tirar muito os pés do chão, solte os ombros e respire confortavelmente.",
              intensityMET: 2.5, symbol: "figure.stand"),
        .init(name: "Socos retos", duration: 6 * 60,
              instruction: "Pés firmes e joelhos destravados. Alterne socos à frente, sem travar os cotovelos. Diminua o ritmo quando precisar.",
              intensityMET: 4.0, symbol: "figure.boxing"),
        .init(name: "Ganchos controlados", duration: 5 * 60,
              instruction: "Faça ganchos curtos e controlados. Mantenha os ombros relaxados e evite girar bruscamente o tronco.",
              intensityMET: 4.0, symbol: "figure.boxing"),
        .init(name: "Lenhador sem peso", duration: 5 * 60,
              instruction: "Leve as mãos em diagonal de um lado para o outro, em amplitude confortável. Não use peso e não force a lombar.",
              intensityMET: 3.5, symbol: "figure.mixed.cardio"),
        .init(name: "Circuito combinado", duration: 6 * 60,
              instruction: "Alterne 30 segundos de socos leves com 30 segundos de lenhador suave. Faça pausas sempre que precisar.",
              intensityMET: 4.0, symbol: "flame"),
        .init(name: "Desaceleração", duration: 4 * 60,
              instruction: "Reduza gradualmente o ritmo, respire devagar e movimente os braços suavemente.",
              intensityMET: 1.8, symbol: "wind")
    ]

    var currentExercise: Exercise { exercises[min(currentIndex, exercises.count - 1)] }
    var totalSeconds: Int { exercises.reduce(0) { $0 + $1.duration } }
    var progress: Double { totalSeconds == 0 ? 0 : Double(elapsedSeconds) / Double(totalSeconds) }
    var elapsedMinutes: Double { Double(elapsedSeconds) / 60.0 }

    // Rough MET-based estimate only; not a measurement or guarantee.
    var estimatedCalories: Int {
        let met = currentExercise.intensityMET
        return Int((met * 3.5 * max(35, weightKg) / 200.0 * elapsedMinutes).rounded())
    }

    func start() { guard !completed else { return }; isRunning = true }
    func pause() { isRunning = false }

    func tick() {
        guard isRunning else { return }
        elapsedSeconds += 1
        if secondsLeft > 0 {
            secondsLeft -= 1
        } else {
            advance()
        }
    }

    func advance() {
        if currentIndex < exercises.count - 1 {
            currentIndex += 1
            secondsLeft = exercises[currentIndex].duration
        } else {
            isRunning = false
            completed = true
        }
    }

    func reset() {
        isRunning = false
        currentIndex = 0
        secondsLeft = exercises[0].duration
        elapsedSeconds = 0
        completed = false
    }

    func skip() {
        if currentIndex < exercises.count - 1 {
            advance()
        } else {
            isRunning = false
            completed = true
        }
    }
}

struct ContentView: View {
    @StateObject private var model = WorkoutModel()
    private let timer = Timer.publish(every: 1, on: .main, in: .common).autoconnect()

    var body: some View {
        ZStack {
            Color(red: 0.055, green: 0.07, blue: 0.10).ignoresSafeArea()
            ScrollView {
                VStack(alignment: .leading, spacing: 20) {
                    header
                    calorieCard
                    if model.completed {
                        completionCard
                    } else {
                        currentWorkoutCard
                        controls
                    }
                    weightCard
                    scheduleCard
                    safetyNote
                }
                .padding(20)
                .frame(maxWidth: 600)
                .frame(maxWidth: .infinity)
            }
        }
        .preferredColorScheme(.dark)
        .onReceive(timer) { _ in model.tick() }
    }

    private var header: some View {
        VStack(alignment: .leading, spacing: 6) {
            HStack {
                Image(systemName: "figure.boxing")
                    .font(.system(size: 28, weight: .bold))
                    .foregroundStyle(.orange)
                Text("SEM IMPACTO")
                    .font(.system(size: 13, weight: .bold, design: .rounded))
                    .tracking(2)
                    .foregroundStyle(.orange)
                Spacer()
                Text("iOS • PROTÓTIPO")
                    .font(.system(size: 10, weight: .semibold))
                    .foregroundStyle(.gray)
            }
            Text("Seu treino, no seu ritmo.")
                .font(.system(size: 29, weight: .bold, design: .rounded))
            Text("Sem saltos. Sem equipamentos. Com pausas quando precisar.")
                .font(.subheadline)
                .foregroundStyle(.secondary)
        }
    }

    private var calorieCard: some View {
        HStack(spacing: 16) {
            ZStack {
                Circle().stroke(.white.opacity(0.10), lineWidth: 8)
                Circle()
                    .trim(from: 0, to: min(1, Double(model.estimatedCalories) / 300.0))
                    .stroke(.orange, style: StrokeStyle(lineWidth: 8, lineCap: .round))
                    .rotationEffect(.degrees(-90))
                Image(systemName: "flame.fill")
                    .font(.title2)
                    .foregroundStyle(.orange)
            }
            .frame(width: 68, height: 68)
            VStack(alignment: .leading, spacing: 4) {
                Text("META DE REFERÊNCIA")
                    .font(.caption.weight(.bold))
                    .foregroundStyle(.secondary)
                Text("\(model.estimatedCalories) kcal")
                    .font(.system(size: 28, weight: .bold, design: .rounded))
                Text("Meta ilustrativa: 300 kcal")
                    .font(.caption)
                    .foregroundStyle(.secondary)
            }
            Spacer(minLength: 0)
        }
        .padding(18)
        .background(Color.white.opacity(0.055), in: RoundedRectangle(cornerRadius: 22))
    }

    private var currentWorkoutCard: some View {
        VStack(alignment: .leading, spacing: 16) {
            HStack {
                Text("TREINO DE HOJE")
                    .font(.caption.weight(.bold))
                    .tracking(1.2)
                    .foregroundStyle(.secondary)
                Spacer()
                Text("\(model.currentIndex + 1) DE \(model.exercises.count)")
                    .font(.caption.weight(.bold))
                    .foregroundStyle(.orange)
            }

            HStack(alignment: .center, spacing: 14) {
                Image(systemName: model.currentExercise.symbol)
                    .font(.system(size: 30, weight: .medium))
                    .foregroundStyle(.orange)
                    .frame(width: 64, height: 64)
                    .background(.orange.opacity(0.12), in: RoundedRectangle(cornerRadius: 18))
                VStack(alignment: .leading, spacing: 5) {
                    Text(model.currentExercise.name)
                        .font(.title3.bold())
                    Text(model.currentExercise.duration / 60 == 1 ? "1 minuto" : "\(model.currentExercise.duration / 60) minutos")
                        .font(.subheadline)
                        .foregroundStyle(.secondary)
                }
            }

            Text(model.currentExercise.instruction)
                .font(.subheadline)
                .foregroundStyle(.white.opacity(0.82))
                .fixedSize(horizontal: false, vertical: true)

            HStack {
                Text("TEMPO RESTANTE")
                    .font(.caption.weight(.bold))
                    .foregroundStyle(.secondary)
                Spacer()
                Text(timeString(model.secondsLeft))
                    .font(.system(size: 28, weight: .bold, design: .rounded).monospacedDigit())
            }
            ProgressView(value: model.progress)
                .tint(.orange)
            Text("\(model.elapsedSeconds / 60) min concluídos de 30 min")
                .font(.caption)
                .foregroundStyle(.secondary)
        }
        .padding(20)
        .background(Color.white.opacity(0.055), in: RoundedRectangle(cornerRadius: 22))
    }

    private var controls: some View {
        HStack(spacing: 10) {
            Button {
                model.isRunning ? model.pause() : model.start()
            } label: {
                Label(model.isRunning ? "Pausar" : "Começar", systemImage: model.isRunning ? "pause.fill" : "play.fill")
                    .font(.headline)
                    .frame(maxWidth: .infinity)
                    .padding(.vertical, 16)
                    .background(.orange, in: RoundedRectangle(cornerRadius: 16))
                    .foregroundStyle(.black)
            }
            Button {
                model.skip()
            } label: {
                Image(systemName: "forward.end.fill")
                    .font(.headline)
                    .frame(width: 56, height: 54)
                    .background(.white.opacity(0.10), in: RoundedRectangle(cornerRadius: 16))
            }
            .accessibilityLabel("Próximo exercício")
            Button {
                model.reset()
            } label: {
                Image(systemName: "arrow.counterclockwise")
                    .font(.headline)
                    .frame(width: 56, height: 54)
                    .background(.white.opacity(0.10), in: RoundedRectangle(cornerRadius: 16))
            }
            .accessibilityLabel("Reiniciar treino")
        }
        .buttonStyle(.plain)
    }

    private var weightCard: some View {
        VStack(alignment: .leading, spacing: 12) {
            Text("PERSONALIZE A ESTIMATIVA")
                .font(.caption.weight(.bold))
                .tracking(1)
                .foregroundStyle(.secondary)
            HStack {
                Text("Peso corporal")
                Spacer()
                Text("\(Int(model.weightKg)) kg")
                    .font(.headline.monospacedDigit())
            }
            Slider(value: $model.weightKg, in: 35...200, step: 1).tint(.orange)
            Text("A estimativa usa peso e intensidade aproximada. Não é uma medição real de calorias.")
                .font(.caption)
                .foregroundStyle(.secondary)
        }
        .padding(18)
        .background(Color.white.opacity(0.055), in: RoundedRectangle(cornerRadius: 22))
    }

    private var scheduleCard: some View {
        VStack(alignment: .leading, spacing: 12) {
            Text("SESSÃO DE 30 MIN")
                .font(.caption.weight(.bold))
                .tracking(1)
                .foregroundStyle(.secondary)
            ForEach(Array(model.exercises.enumerated()), id: \.offset) { index, exercise in
                HStack(spacing: 12) {
                    Image(systemName: index < model.currentIndex || model.completed ? "checkmark.circle.fill" : "circle")
                        .foregroundStyle(index < model.currentIndex || model.completed ? .green : .gray)
                    Text(exercise.name)
                    Spacer()
                    Text("\(exercise.duration / 60) min")
                        .foregroundStyle(.secondary)
                }
                .font(.subheadline)
            }
        }
        .padding(18)
        .background(Color.white.opacity(0.055), in: RoundedRectangle(cornerRadius: 22))
    }

    private var completionCard: some View {
        VStack(spacing: 12) {
            Image(systemName: "checkmark.seal.fill")
                .font(.system(size: 46))
                .foregroundStyle(.green)
            Text("Treino concluído!")
                .font(.title2.bold())
            Text("Mandou bem. Registre como você se sentiu e descanse.")
                .multilineTextAlignment(.center)
                .foregroundStyle(.secondary)
            Button("Fazer novamente") { model.reset() }
                .buttonStyle(.borderedProminent)
                .tint(.orange)
                .foregroundStyle(.black)
        }
        .frame(maxWidth: .infinity)
        .padding(24)
        .background(Color.white.opacity(0.055), in: RoundedRectangle(cornerRadius: 22))
    }

    private var safetyNote: some View {
        VStack(alignment: .leading, spacing: 7) {
            Label("Treino adaptável", systemImage: "heart.text.square")
                .font(.subheadline.bold())
            Text("Faça os movimentos sem dor e respire normalmente. Diminua o ritmo ou pause quando necessário. Pare e procure ajuda se sentir dor no peito, tontura ou falta de ar intensa ou incomum. A meta de 300 kcal não é garantida.")
                .font(.caption)
                .foregroundStyle(.secondary)
        }
        .padding(16)
        .background(.orange.opacity(0.08), in: RoundedRectangle(cornerRadius: 18))
    }

    private func timeString(_ seconds: Int) -> String {
        String(format: "%02d:%02d", seconds / 60, seconds % 60)
    }
}

@main
struct TreinoSemImpactoApp: App {
    var body: some Scene {
        WindowGroup {
            ContentView()
        }
    }
}
