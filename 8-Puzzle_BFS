package com.puzzle;

import java.util.ArrayDeque;
import java.util.Arrays;
import java.util.Queue;

public class Puzzle {
	
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
			return "State [currBlank=" + currBlank + ", state=" + Arrays.toString(state) + ", parentBlank="
					+ parentBlank + "]";
		}

		Pair currBlank;
		int[][] state=new int[3][3];
		Pair parentBlank;
		
		State(Pair currBlank, int[][] state, Pair parentBlank){
			//currBlank
			this.currBlank=currBlank;
			
			//array
			for(int i=0; i<3; i++) {
				for(int j=0; j<3; j++) {
					this.state[i][j]=state[i][j];
				}
			}
			
			//parentBlank
			this.parentBlank=parentBlank;
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
		
		return 1;
		
		
		
	}
	
	public static void solve(int[][] arr, int[][] endGoal, Pair startPos) {
		
		Queue<State> q=new ArrayDeque<>();
		q.add(new State(startPos, arr, new Pair(-1, -1)));
		int iter=0;
		
		while(q.size()!=0) {
			State s=q.peek();
			//parent Blank
			Pair currBlank=s.currBlank;
			
			int rows=s.state.length;
			int cols=s.state[0].length;
			
			//check if goal is found
//			int res=checkIfGoalFound(s.state, endGoal);
//			if(res==1) {
//				System.out.println("Goal Found");
//				System.out.println("iter: "+iter);
//				break;
//			}
			
			//print array
			System.out.println("iter: "+(iter+1));
			
			for(int i=0; i<3; i++) {
				for(int j=0; j<3; j++) {
					System.out.print(s.state[i][j]+" ");
				}
				System.out.println();
			}
			System.out.println(s.toString());
			System.out.println();
			
			
			//parent blank
			Pair parentBlank=s.parentBlank;
			
			//find neighbors
			//left
			if(currBlank.j!=0) {
				
				if(currBlank.j-1 == parentBlank.j && currBlank.i == parentBlank.i) {
					//do nothing
				}
				else {
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
					
					//check goal
					int res=checkIfGoalFound(temp, endGoal);
					if(res==1) {
						System.out.println("Goal Found");
						System.out.println("iter: "+iter);
						break;
					}
					
					Pair parent;
					
					if(iter==0) {
						parent=currBlank;
					}
					else {
						parent=parentBlank;
					}
					
					q.offer(new State(pos, temp, parent));
				}
			}
			//top
			if(currBlank.i!=0) {
				
				if(currBlank.i-1 == parentBlank.i && currBlank.j == parentBlank.j) {
					//do nothing
				}
				else {
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
					
					//check goal
					int res=checkIfGoalFound(temp, endGoal);
					if(res==1) {
						System.out.println("Goal Found");
						System.out.println("iter: "+iter);
						break;
					}
					
					Pair parent;
					if(iter==0) {
						parent=currBlank;
					}
					else {
						parent=parentBlank;
					}
					
					q.offer(new State(pos, temp, parent));
				}
				
			}
			//bottom
			if(currBlank.i!=rows-1) {
				
				if(currBlank.i+1 == parentBlank.i && currBlank.j == parentBlank.j) {
					//do nothing
				}
				else {
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
					
					//check goal
					int res=checkIfGoalFound(temp, endGoal);
					if(res==1) {
						System.out.println("Goal Found");
						System.out.println("iter: "+iter);
						break;
					}
					
					Pair parent;
					if(iter==0) {
						parent=currBlank;
					}
					else {
						parent=parentBlank;
					}
					
					q.offer(new State(pos, temp, parent));
					
				}
			}
			//right
			if(currBlank.j!=cols-1) {
				
				if(currBlank.j+1!=parentBlank.j && currBlank.i==parentBlank.i) {
					//do nothing
				}
				else {
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
					
					//check goal
					int res=checkIfGoalFound(temp, endGoal);
					if(res==1) {
						System.out.println("Goal Found");
						System.out.println("iter: "+iter);
						break;
					}
					
					Pair parent;
					if(iter==0) {
						parent=currBlank;
					}
					else {
						parent=parentBlank;
					}
					
					q.offer(new State(pos, temp, parent));
				}
			}
			
			
			q.poll();
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
