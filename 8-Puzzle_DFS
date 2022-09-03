package com.puzzle;

import java.util.ArrayDeque;
import java.util.ArrayList;
import java.util.Arrays;
import java.util.Queue;
import java.util.Stack;

import com.puzzle.Puzzle.Pair;
import com.puzzle.Puzzle.State;

public class PuzzleDFS {

	public static class Pair{
		int i; 
		int j;
		
		Pair(int i, int j){
			this.i=i;
			this.j=j;
		}

		@Override
		public String toString() {
			return "Pair [i=" + i + ", j=" + j + "]";
		}
	}
	
	public static class State{
		
		@Override
		public String toString() {
			return "State [currBlank=" + currBlank + ", state=" + Arrays.toString(state) + "]";
		}

		Pair currBlank;
		int[][] state=new int[3][3];
	
		State(Pair currBlank, int[][] state){
			//currBlank
			this.currBlank=currBlank;
			
			//array
			for(int i=0; i<3; i++) {
				for(int j=0; j<3; j++) {
					this.state[i][j]=state[i][j];
				}
			}
		}
	}
	
	public static int checkIfGoalFound(int[][] arr, int[][] goal) {
		
		int rows=arr.length;
		int cols=arr[0].length;
		
		for(int i=0; i<rows; i++) {
			for(int j=0; j<arr[0].length; j++) {
				if(arr[i][j]!=goal[i][j]) {
					return 0;
				}
			}
		}
		
		System.out.println("=================================");
		
		for(int i=0; i<rows; i++) {
			for(int j=0; j<arr[0].length; j++) {
				System.out.print(arr[i][j]+" ");
			}
			System.out.println();
		}
		
		
		return 1;
	}
	
	public static int alreadyExplored(int[][] arr, ArrayList<ArrayList<Integer>> exploredStates) {
		
		int k=0;
		boolean isSame=true;
		int count=0;
		
		for(int i=0; i<exploredStates.size(); i++) {
			isSame=true;
			k=0;
			ArrayList<Integer> temp=exploredStates.get(i);
			
			for(int m=0; m<3; m++) {
				for(int n=0; n<3; n++) {
					if(arr[m][n]!=temp.get(k)) {
						isSame=false;
						break;
					}
					k++;
				}
			}
			
			if(isSame==true) {
				count++;
			}
		}
		
		if(count==0) {
			return 0;
		}
		else {
			return 1;
		}
	
	}
	
	public static void solve(int[][] arr, int[][] endGoal, Pair startPos) {
		ArrayList<ArrayList<Integer>> exploredStates=new ArrayList<>();
		Stack<State> st=new Stack<>();
		
		//add initial state
		st.push(new State(startPos, arr));
		
		//add initial explored state
		ArrayList<Integer> tem=new ArrayList<>();
		for(int i=0; i<3; i++) {
			for(int j=0; j<3; j++) {
				tem.add(st.peek().state[i][j]);
			}
		}
		exploredStates.add(tem);
		
		int iter=1;
		
		while(st.size()!=0) {
			State s=st.pop();
			//parent Blank
			Pair currBlank=s.currBlank;
			
			int rows=s.state.length;
			int cols=s.state[0].length;
			
			//print array
			System.out.println("iter: "+(iter));
			
			for(int i=0; i<3; i++) {
				for(int j=0; j<3; j++) {
					System.out.print(s.state[i][j]+" ");
				}
				System.out.println();
			}
			
			System.out.println();
			
			
			//find neighbors
			//left
			if(currBlank.j!=0) {
					Pair pos=new Pair(currBlank.i, currBlank.j-1);
					
					//swap respective position
					int temp[][]=new int[rows][cols];
					
					//current array
					for(int i=0; i<rows; i++) {
						for(int j=0; j<cols; j++) {
							temp[i][j]=s.state[i][j];
						}
					}
					
					int swap=temp[currBlank.i][currBlank.j];
					temp[currBlank.i][currBlank.j]=temp[currBlank.i][currBlank.j-1];
					temp[currBlank.i][currBlank.j-1]=swap;
					
					//check if the state already explored
					int explored=alreadyExplored(temp, exploredStates);
					
					if(explored!=1) {
						
						//check goal
						int res=checkIfGoalFound(temp, endGoal);
						if(res==1) {
							System.out.println("Goal Found");
							System.out.println("Total iterations: "+(iter+1));
							break;
						}
						
						//put state into queue
						st.push(new State(pos, temp));
						
						//add to explored states
						ArrayList<Integer> t=new ArrayList<>();
						
						for(int i=0; i<rows; i++) {
							for(int j=0; j<cols; j++) {
								t.add(temp[i][j]);
							}
						}
						exploredStates.add(t);
					}
			}
			//top
			if(currBlank.i!=0) {

					Pair pos=new Pair(currBlank.i-1, currBlank.j);
					
					//swap respective position
					
					int temp[][]=new int[rows][cols];
					
					//current array
					for(int i=0; i<rows; i++) {
						for(int j=0; j<cols; j++) {
							temp[i][j]=s.state[i][j];
						}
					}
					
					int swap=temp[currBlank.i][currBlank.j];
					temp[currBlank.i][currBlank.j]=temp[currBlank.i-1][currBlank.j];
					temp[currBlank.i-1][currBlank.j]=swap;
					
					//check if the state already explored
					int explored=alreadyExplored(temp, exploredStates);
					
					if(explored!=1) {
						//check goal
						int res=checkIfGoalFound(temp, endGoal);
						if(res==1) {
							System.out.println("Goal Found");
							System.out.println("Total iterations: "+(iter+1));
							break;
						}
						
						//put state into queue
						st.push(new State(pos, temp));
						
						//add to explored states
						ArrayList<Integer> t=new ArrayList<>();
						
						for(int i=0; i<rows; i++) {
							for(int j=0; j<cols; j++) {
								t.add(temp[i][j]);
							}
						}
						exploredStates.add(t);
					}
			}
			//bottom
			if(currBlank.i!=rows-1) {
				
					Pair pos=new Pair(currBlank.i+1, currBlank.j);
					
					//swap respective position
					int temp[][]=new int[rows][cols];
					
					//current array
					for(int i=0; i<rows; i++) {
						for(int j=0; j<cols; j++) {
							temp[i][j]=s.state[i][j];
						}
					}
					
					int swap=temp[currBlank.i][currBlank.j];
					temp[currBlank.i][currBlank.j]=temp[currBlank.i+1][currBlank.j];
					temp[currBlank.i+1][currBlank.j]=swap;
					
					//check if the state already explored
					int explored=alreadyExplored(temp, exploredStates);
					
					if(explored!=1) {
						//check goal
						int res=checkIfGoalFound(temp, endGoal);
						if(res==1) {
							System.out.println("Goal Found");
							System.out.println("Total iterations: "+(iter+1));
							break;
						}
						
						//put state into queue
						st.push(new State(pos, temp));
						
						//add to explored states
						ArrayList<Integer> t=new ArrayList<>();
						
						for(int i=0; i<rows; i++) {
							for(int j=0; j<cols; j++) {
								t.add(temp[i][j]);
							}
						}
						exploredStates.add(t);
					}
			}
			//right
			if(currBlank.j!=cols-1) {
				
					Pair pos=new Pair(currBlank.i, currBlank.j+1);
					
					//swap respective position
					int temp[][]=new int[rows][cols];
					
					//current array
					for(int i=0; i<rows; i++) {
						for(int j=0; j<cols; j++) {
							temp[i][j]=s.state[i][j];
						}
					}
					
					int swap=temp[currBlank.i][currBlank.j];
					temp[currBlank.i][currBlank.j]=temp[currBlank.i][currBlank.j+1];
					temp[currBlank.i][currBlank.j+1]=swap;
					
					//check if the state already explored
					int explored=alreadyExplored(temp, exploredStates);
					
					if(explored!=1) {
						//check goal
						int res=checkIfGoalFound(temp, endGoal);
						if(res==1) {
							System.out.println("Goal Found");
							System.out.println("Total iterations: "+(iter+1));
							break;
						}
						
						//put state into queue
						st.push(new State(pos, temp));
						
						//add to explored states
						ArrayList<Integer> t=new ArrayList<>();
						
						for(int i=0; i<rows; i++) {
							for(int j=0; j<cols; j++) {
								t.add(temp[i][j]);
							}
						}
						exploredStates.add(t);
					}
			}
			
			
			//st.pop();
			iter++;
		}
	}
	
	public static void main(String[] args) {
		
		int[][] arr= {{2, 8, 3},
				  {1, 6, 4},
				{7, 0, 5}};
	
		int[][] endGoal= {{1, 2, 3},
					  {8, 0, 4},
					  {7, 6, 5}};
	
		solve(arr, endGoal, new Pair(2,1));

	}

}
