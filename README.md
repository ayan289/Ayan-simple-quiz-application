public class QuizController {

    private QuizModel model;
    private QuizView view;
    private int correctAnswers = 0;

    public QuizController(QuizModel model, QuizView view) {
        this.model = model;
        this.view = view;
    }

    // Start the quiz
    public void startQuiz() {
        int totalQuestions = model.getTotalQuestions();

        for (int i = 0; i < totalQuestions; i++) {
            String question = model.getQuestion(i);
            String[] options = model.getOptions(i);

            view.displayQuestion(question, options);
            int userAnswer = view.getUserAnswer();

            if (userAnswer == model.getCorrectAnswer(i)) {
                correctAnswers++;
            }
        }

        view.displayResult(correctAnswers, totalQuestions);
    }
}
