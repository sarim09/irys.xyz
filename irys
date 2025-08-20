// src/App.js
import React, { useState } from 'react';

/*
  Irys Quiz App (single-file React component)
  - Exported items for testing: QUESTIONS, checkAnswers, TEST_CASES
  - This version removes all emoji and non-ASCII characters to avoid parser issues.
*/

export const QUESTIONS = [
  {
    question: 'What is Irys primarily known for?',
    options: ['Decentralized Storage', 'Social Media', 'Gaming Platform', 'NFT Marketplace'],
    answer: 0,
  },
  {
    question: 'Which layer is Irys built on?',
    options: ['Layer 0', 'Layer 1', 'Layer 2', 'App Chain'],
    answer: 1,
  },
  {
    question: 'What is Irys used for?',
    options: ['Permanent Data Uploads', 'Video Streaming', 'DEX Swaps', 'AI Models'],
    answer: 0,
  },
  {
    question: 'Which token standard does Irys often integrate with?',
    options: ['ERC-20', 'ERC-721', 'ERC-1155', 'All of the above'],
    answer: 3,
  },
  {
    question: 'What makes Irys different from IPFS?',
    options: ['Data permanence and economic model', 'Faster uploads', 'Better UI', 'Uses Ethereum only'],
    answer: 0,
  },
  {
    question: 'What is the official website of Irys?',
    options: ['irys.xyz', 'irys.io', 'irys.org', 'irys.network'],
    answer: 0,
  },
];

// Utility function for unit testing: pass an array of selected option indexes and get the score
export function checkAnswers(selectedIndices) {
  if (!Array.isArray(selectedIndices)) {
    throw new Error('selectedIndices must be an array');
  }
  let score = 0;
  for (let i = 0; i < QUESTIONS.length; i++) {
    if (selectedIndices[i] === QUESTIONS[i].answer) score++;
  }
  return score;
}

// Test cases to validate behavior. Existing cases preserved; added one more.
export const TEST_CASES = [
  { name: 'all correct', answers: QUESTIONS.map(q => q.answer), expected: QUESTIONS.length },
  { name: 'all wrong', answers: QUESTIONS.map(() => -1), expected: 0 },
  { name: 'alternate correct', answers: QUESTIONS.map((q, i) => (i % 2 === 0 ? q.answer : -1)), expected: Math.ceil(QUESTIONS.length / 2) },
  { name: 'first three correct', answers: QUESTIONS.map((q, i) => (i < 3 ? q.answer : -1)), expected: Math.min(3, QUESTIONS.length) },
];

const App = () => {
  const [current, setCurrent] = useState(0);
  const [score, setScore] = useState(0);
  const [finished, setFinished] = useState(false);

  const handleAnswer = index => {
    if (index === QUESTIONS[current].answer) {
      setScore(prev => prev + 1);
    }
    if (current + 1 < QUESTIONS.length) {
      setCurrent(prev => prev + 1);
    } else {
      setFinished(true);
    }
  };

  const reset = () => {
    setCurrent(0);
    setScore(0);
    setFinished(false);
  };

  return (
    <div className="min-h-screen flex flex-col items-center justify-center bg-gray-900 text-white p-4">
      <div className="bg-gray-800 p-6 rounded-2xl shadow-lg w-full max-w-lg">
        <h1 className="text-2xl font-bold text-center mb-6">Irys Quiz</h1>

        {!finished ? (
          <div>
            <h2 className="text-lg mb-4">
              Q{current + 1}: {QUESTIONS[current].question}
            </h2>
            <div className="grid gap-3">
              {QUESTIONS[current].options.map((option, idx) => (
                <button
                  key={idx}
                  onClick={() => handleAnswer(idx)}
                  className="bg-blue-600 hover:bg-blue-700 px-4 py-2 rounded-xl text-left"
                >
                  {option}
                </button>
              ))}
            </div>
          </div>
        ) : (
          <div className="text-center">
            <h2 className="text-xl font-semibold mb-4">Quiz Finished!</h2>
            <p className="text-lg">Your Score: {score} / {QUESTIONS.length}</p>
            <div className="mt-4">
              <button onClick={reset} className="bg-green-600 hover:bg-green-700 px-4 py-2 rounded-xl">
                Retry
              </button>
            </div>
          </div>
        )}
      </div>

      <footer className="mt-6 text-center text-sm text-gray-400">
        Made with Love by Blazinghalo
      </footer>
    </div>
  );
};

export default App;
