import React, { useState } from 'react';
import { Card, CardHeader, CardTitle, CardContent } from '@/components/ui/card';
import { BarChart, Bar, XAxis, YAxis, Tooltip, ResponsiveContainer } from 'recharts';
import { AlertCircle, CheckCircle } from 'lucide-react';

const NewsAnalyzer = () => {
  const [newsText, setNewsText] = useState('');
  const [analysisResult, setAnalysisResult] = useState(null);
  
  // Simulated analysis function (in real app, this would call your ML model)
  const analyzeNews = () => {
    // Simulate ML model prediction
    const credibilityScore = Math.random();
    const subjectAnalysis = {
      'Political': 0.45,
      'Economic': 0.25,
      'Technology': 0.15,
      'Health': 0.15
    };
    
    setAnalysisResult({
      credibilityScore,
      subjectAnalysis: Object.entries(subjectAnalysis).map(([name, value]) => ({
        name,
        value: value * 100
      }))
    });
  };

  return (
    <div className="w-full max-w-4xl mx-auto p-4 space-y-4">
      <Card>
        <CardHeader>
          <CardTitle>News Credibility Analyzer</CardTitle>
        </CardHeader>
        <CardContent>
          <textarea
            className="w-full h-32 p-2 border rounded"
            placeholder="Paste news article text here..."
            value={newsText}
            onChange={(e) => setNewsText(e.target.value)}
          />
          <button
            className="mt-4 px-4 py-2 bg-blue-500 text-white rounded"
            onClick={analyzeNews}
          >
            Analyze Text
          </button>
          
          {analysisResult && (
            <div className="mt-6 space-y-6">
              <div className="flex items-center space-x-4">
                {analysisResult.credibilityScore > 0.5 ? (
                  <CheckCircle className="text-green-500" size={24} />
                ) : (
                  <AlertCircle className="text-red-500" size={24} />
                )}
                <div>
                  <h3 className="text-lg font-semibold">
                    Credibility Score: {(analysisResult.credibilityScore * 100).toFixed(1)}%
                  </h3>
                  <p className="text-gray-600">
                    {analysisResult.credibilityScore > 0.5 
                      ? 'This article appears to be credible'
                      : 'This article may contain misleading information'}
                  </p>
                </div>
              </div>
              
              <div className="h-64">
                <h3 className="text-lg font-semibold mb-2">Subject Analysis</h3>
                <ResponsiveContainer width="100%" height="100%">
                  <BarChart data={analysisResult.subjectAnalysis}>
                    <XAxis dataKey="name" />
                    <YAxis />
                    <Tooltip />
                    <Bar dataKey="value" fill="#4f46e5" />
                  </BarChart>
                </ResponsiveContainer>
              </div>
            </div>
          )}
        </CardContent>
      </Card>
    </div>
  );
};

export default NewsAnalyzer;
